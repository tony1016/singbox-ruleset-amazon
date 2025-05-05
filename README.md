# Amazon IP 规则集 for Sing-box (Android TV Netflix 代理场景优化版)

## 文件说明
- **文件名**：`amazonip.json`  
- **适用场景**：Android TV 设备绕过 Netflix 代理检测  
- **核心作用**：精准路由 Amazon AWS IP 流量，避免 Netflix 检测到 VPN/代理  

## 技术背景
当 Android TV 版 Netflix 检测到代理时：
1. 会屏蔽 VPN 出口 IP
2. 要求关闭代理才能播放
3. 本规则集通过精确分流 Amazon AWS IP 解决此问题

## 特性优化
✔️ 特别处理 Netflix 使用的 AWS EC2 IP 段  
✔️ 包含 AWS Global Accelerator 节点  
✔️ 排除非视频流媒体相关的 AWS IP  
✔️ 针对 Android TV 低功耗设备优化 CIDR 合并  

## 使用建议
1. 在 Sing-box 配置中优先匹配此规则集
2. 建议配合 `geosite:netflix` 域名规则使用
3. 更新频率建议每周至少 1 次（Netflix 常更换服务器 IP）

## 典型错误排查
如果仍出现代理警告：
1. 检查规则集加载是否生效
2. 测试 AWS IP 是否被 Netflix 特殊标记
3. 尝试切换其他 AWS 区域 IP 段

> ⚠️ 注意：部分国家区版的 Netflix 会深度检测 AWS 机房 IP，此时需要配合 WARP 等工具使用
