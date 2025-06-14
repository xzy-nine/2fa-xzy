2FA验证码管家 - 浏览器扩展

一个功能强大的2FA验证码管理浏览器扩展，支持WebDAV云端同步、本地存储、二维码扫描和生物识别验证。

## 🚀 主要功能

### 核心功能

- **智能填充**: 自动识别2FA验证码输入框，一键填充验证码
- **本地优先**: 默认本地加密存储，保证离线使用和快速访问
- **云端备份**: 通过WebDAV服务器自动备份配置，支持多设备同步
- **二维码扫描**: 支持摄像头扫描和屏幕识别两种方式导入配置

### 安全功能

- **加密存储**: 使用AES-GCM加密算法保护敏感数据
- **生物识别**: 支持Windows Hello等生物识别验证
- **分层保护**: 配置列表不加密，密钥数据强加密
- **自定义密钥**: 支持用户自定义加密密钥

### 存储策略

- **本地优先**: 所有配置默认保存到本地加密存储，确保离线可用
- **自动备份**: 配置WebDAV后，新增配置自动备份到云端
- **智能合并**: 从云端恢复时自动去重，避免重复配置
- **来源标识**: 界面显示配置来源（💾本地存储 / ☁️云端备份）

### 智能特性

- **自动识别**: 智能识别页面中的2FA输入框
- **记忆功能**: 记住每个网站使用的配置，下次自动匹配
- **实时更新**: 本地验证码实时显示剩余时间和自动刷新
- **右键菜单**: 便捷的右键菜单快速操作

## 📦 安装使用

### 开发环境安装

1. 克隆或下载此项目
2. 打开Chrome浏览器，进入 `chrome://extensions/`
3. 开启"开发者模式"
4. 点击"加载已解压的扩展程序"
5. 选择项目根目录

### 首次配置

1. 点击扩展图标打开弹出页
2. 切换到"设置"标签页
3. 配置WebDAV服务器信息（可选）
4. 设置加密密钥（可选，留空使用简单加密）
5. 启用生物识别验证（可选）

## 🔧 使用指南

### 1. 导入2FA配置

#### 方法一：扫描二维码

1. 点击扩展图标，切换到"扫描"标签页
2. 选择"摄像头扫描"或"屏幕识别"
3. 扫描2FA设置页面的二维码
4. 输入配置名称并保存

#### 方法二：手动输入

1. 在设置中手动添加配置
2. 输入密钥、账户名、发行方等信息
3. 保存配置

### 2. 填充验证码

#### 快速填充

1. 在需要2FA验证的网页上点击验证码输入框
2. 点击扩展图标
3. 如果已有保存的配置，点击"快速填充"
4. 验证码自动填入输入框

#### 选择配置填充

1. 点击验证码输入框
2. 点击扩展图标
3. 进行身份验证（如果启用）
4. 点击"填充验证码"
5. 选择要使用的配置
6. 验证码自动填入

### 3. 本地验证码查看

1. 切换到"本地"标签页
2. 进行身份验证
3. 查看实时验证码和倒计时
4. 点击验证码复制到剪贴板

## ⚙️ 配置说明

### WebDAV设置

- **服务器地址**: 您的WebDAV服务器URL
- **用户名**: WebDAV账户用户名
- **密码**: WebDAV账户密码

支持的WebDAV服务：

- Nextcloud
- ownCloud
- 坚果云
- 其他兼容WebDAV协议的服务

### 加密设置

- **简单加密**: 留空密钥时使用，适合个人使用
- **自定义密钥**: 输入强密码，提供更高安全性
- **生物识别**: 启用后使用Windows Hello等进行身份验证

### 本地存储

- 允许将常用配置保存在浏览器本地存储
- 支持离线使用
- 需要身份验证才能查看

## 🔒 安全机制

### 数据保护

1. **分层加密**: 配置列表明文存储便于管理，密钥数据强加密保护
2. **密钥派生**: 使用PBKDF2算法派生加密密钥
3. **安全随机**: 使用加密安全的随机数生成器
4. **内存保护**: 敏感数据使用后立即清除

### 访问控制

1. **生物识别**: 支持平台原生的生物识别API
2. **会话管理**: 认证状态有时效性，需要定期重新认证
3. **权限最小化**: 只请求必要的浏览器权限

### 传输安全

1. **HTTPS传输**: WebDAV通信强制使用HTTPS
2. **端到端加密**: 数据在客户端加密后再传输
3. **完整性校验**: 数据包含完整性校验信息

## 🌐 兼容性

### 浏览器支持

仅chrome内核

文件结构

~~~~
2fa-xzy/
├── html/
│   ├── popup.html              # 弹出页面
│   ├── setting.html            # 设置页面
│   └── js/
│       ├── index.js            # 核心入口文件 - 统一导出所有模块
│       ├── crypto.js           # 加密解密模块
│       ├── totp.js             # TOTP验证码生成模块
│       ├── webdav.js           # WebDAV客户端模块
│       ├── local-storage.js    # 本地存储管理模块
│       ├── qr-scanner.js       # 二维码扫描模块
│       ├── popup.js            # 弹出页面管理模块
│       ├── setting.js          # 设置页面管理模块
│       ├── background.js       # 后台脚本模块
│       └── content.js          # 内容脚本模块
├── css/
│   ├── common.css              # 基础CSS文件 - 导入其他CSS模块
│   ├── variables.css           # CSS变量定义
│   ├── reset.css               # CSS重置样式
│   ├── components.css          # 组件样式
│   ├── utilities.css           # 工具类样式
│   ├── popup.css               # 弹出页面样式
│   └── settings.css            # 设置页面样式
└── manifest.json
~~~~

## 🔧 技术架构更新 (2025年6月)

### TOTP库升级

项目已从自实现的TOTP算法升级到使用成熟的 [OTPAuth](https://github.com/hectorm/otpauth) 库：

#### 主要改进

- ✅ **成熟稳定**: 使用经过广泛测试的OTPAuth库（9.4.0版本）
- ✅ **标准兼容**: 完全符合RFC 4226 (HOTP) 和 RFC 6238 (TOTP) 标准
- ✅ **功能增强**: 支持更多算法和配置选项
- ✅ **向后兼容**: 保留了原有的API接口和功能

#### 技术架构

```html
<!-- 库加载顺序 -->
<script src="./js/lib/otpauth.umd.min.js"></script>  <!-- OTPAuth库 -->
<script src="./js/totp.js"></script>                 <!-- TOTP适配器 -->
```

#### 使用方式

```javascript
// 原有API保持不变
const totp = new TOTPGenerator();
const code = await totp.generateTOTP(secret);
const currentInfo = await totp.getCurrentCode(secret);
```

### 全局变量模块系统

项目已从ES6模块系统迁移到全局变量模块系统，以确保与Chrome扩展的Service Worker环境完全兼容：

#### 主要改进

- ✅ **Service Worker兼容**: 完全支持Chrome扩展的Service Worker环境
- ✅ **无ES6依赖**: 避免了ES6模块的兼容性问题
- ✅ **统一加载**: 通过全局变量统一管理所有模块
- ✅ **向后兼容**: 保留了原有的API接口

#### 模块加载方式

```html
<!-- 按依赖顺序加载 -->
<script src="./js/crypto.js"></script>
<script src="./js/totp.js"></script>
<script src="./js/local-storage.js"></script>
<script src="./js/webdav.js"></script>
<script src="./js/qr-scanner.js"></script>
<script src="./js/popup.js"></script>     <!-- 弹出页面 -->
<script src="./js/setting.js"></script>   <!-- 设置页面 -->
<script src="./js/main.js"></script>      <!-- 主入口 -->
```

#### 使用方式

```javascript
// 直接使用全局变量
const crypto = new CryptoManager();
const totp = new TOTPGenerator();

// 或使用别名（向后兼容）
const crypto2 = new Crypto();
const totp2 = new TOTP();

// 使用统一应用实例
await app.init();
const utils = app.getUtils();
```

详细文档请参考：[全局变量模块系统使用指南](./GLOBAL_MODULE_GUIDE.md)
