# greencloud vps：低价 KVM 与 Windows VPS 怎么选，套餐价格、退款限制和机房现状一次说清

搜 greencloud vps 的人，多半卡在两个问题上：这家的便宜套餐到底什么配置、什么价格，以及下单之后会不会被条款坑。先把结论放前面：GreenCloud（圈内叫绿云）是一家 2013 年成立的 VPS 服务商，主力卖点是低价 KVM 套餐和 Windows 远程桌面实例，Budget KVM 系列月付 $6 起，全球 30 多个机房，拿过 LowEndTalk 的 "#1 Top Provider" 和 "#1 Most Stable Provider"。但它有两条硬限制必须提前知道：促销套餐一律不退款，CPU 连续跑满 30 分钟会被限速甚至关机。这两条后面会展开讲。

> **选购速览**：预算有限、只需要跑个网站或小服务的，选 Budget KVM 的 SSDKVM-1（1 核 / 1GB 内存 / 15GB SSD，$6/月）就够用；需要 Windows 远程桌面的，普通版 US1 月付 $8 起。想直接对比所有档位，👉 [查看绿云 $6/月起的 Budget KVM 套餐](https://greencloudvps.com/billing/aff.php?aff=6679)。

## GreenCloud VPS 是什么来头

GreenCloud 是一家 IaaS 服务商，卖 Linux VPS、Windows VPS、macOS VPS 和独立服务器，2013 年成立，据中文社区资料总部在越南河内。它的硬件是自有的企业级设备，CPU 用 AMD EPYC Milan/Genoa 和 Ryzen，存储是 NVMe 4.0 配 RAID-10，官方页面标注 600+ Gbps 聚合带宽、覆盖 4 大洲 30 个地点 32 个数据中心，网络和电力在线率承诺 99.99%。

这套配置在低价 VPS 圈子里算是比较扎实的。很多同价位商家用的是老款至强加 SATA 盘，绿云的 Ryzen 系列单核性能明显更强，跑数据库和动态网站有实际优势。售后方面，官网称工单平均响应 9 分钟、支持 24/7；中文社区的观察更细一些：它是 Unmanaged 定位，技术人员只负责底层网络和母机稳定，操作系统里的问题不帮你排查，遇到节假日回复会变慢。买之前对这一点要有预期。

## 套餐与价格：官网能买到什么

绿云的产品线分两大块：Linux 走 KVM 虚拟化，Windows 走 Hyper-V。下面两张表是目前官网公开报价、可以逐档核验的两条主力线。

**Budget KVM VPS（Linux，10Gbps 端口，美/欧/APAC 可选）**

| 套餐 | 配置 | 月流量 | 价格 | 购买 |
| --- | --- | --- | --- | --- |
| SSDKVM-1 | 1 核 / 1GB / 15GB SSD | 1.5TB | $6/月 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| SSDKVM-2 | 1 核 / 2GB / 15GB SSD | 2TB | $10/月 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| SSDKVM-3 | 2 核 / 4GB / 30GB SSD | 4TB | $20/月 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| SSDKVM-4 | 4 核 / 8GB / 60GB SSD | 8TB | $40/月 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| SSDKVM-5 | 8 核 / 16GB / 120GB SSD | 12TB | $80/月 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |

**Budget Windows VPS（Windows Server 2022，1Gbps 端口，不限流量）**

| 套餐 | 配置 | 价格 | 计费要求 | 购买 |
| --- | --- | --- | --- | --- |
| US1 | 1 核 / 1GB / 25GB SSD | $8/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US1.5 | 1 核 / 1.5GB / 30GB SSD | $12/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US2 | 2 核 / 2GB / 40GB SSD | $16/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US3 | 2 核 / 3GB / 60GB SSD | $24/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US4 | 4 核 / 4GB / 80GB SSD | $32/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US5 | 5 核 / 5GB / 100GB SSD | $40/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| US6 | 6 核 / 6GB / 120GB SSD | $48/月 | 可月付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| Budget-1（SuperSaving） | 1 核 / 2GB / 25GB SSD | $10/月 | 至少季付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| Budget-2（SuperSaving） | 2 核 / 4GB / 40GB SSD | $20/月 | 至少季付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |
| Budget-3（SuperSaving） | 4 核 / 8GB / 80GB SSD | $40/月 | 至少季付 | [ 购买](https://greencloudvps.com/billing/aff.php?aff=6679) |

Windows 线里藏着一个多数测评没讲透的选择题：SuperSaving 版和普通版价格接近，但内存直接翻倍——$10 档给 2GB（普通版 $8 档只有 1GB），$20 档给 4GB，$40 档给 8GB。代价是必须按季度起付。如果你确定要用三个月以上，SuperSaving 明显更划算；只是临时挂个工具用一个月，老老实实买普通版 US1。

除了上面这两条线，官网还有几条产品线只展示配置不展示标准价：EPYC VDS（独占资源 + 10Gbps）、Ryzen VPS（高频 CPU）、10Gbps VPS、Storage 大容量存储 VPS（SATA RAID-10），Windows 侧还有 SEO Optimized、Forex（针对 MT4/MT5 优化）、Managed 托管版和 10Gbps 版。这些需要到官网对应页面确认实时价格。

## 下单前必须知道的四个限制

绿云便宜的前提是几个写在条款里的规则，买之前不看，后面容易产生纠纷。

1. **促销套餐不退款。** 官方政策是所有特价、大促、促销套餐一律不退款；普通原价月付套餐也只在 7 天内、且确实是系统故障的前提下才能申请退款。抱着“买来试试、不好就退”心态的人，绿云不合适。想验证线路质量，先用 $6 的 SSDKVM-1 买一个月，成本可控。
2. **CPU 不允许长期跑满。** 服务条款规定，连续 30 分钟以上占满 100% vCPU（比如长时间压制视频、跑高频量化、编译大项目），系统会自动限速甚至强行关机。24 小时满载的业务请直接看独占资源的 EPYC VDS 或独立服务器。
3. **APAC 机房流量砍半。** 同样是 SSDKVM 系列，美欧机房给 1.5TB–12TB 月流量，APAC 机房只有 750GB–6TB，正好是一半。选日本、新加坡、香港节点前先看清楚这一行。
4. **附加资源有上限。** 缺内存可以加，$3/1GB 内存/月、$3/核/月、$3/10GB SSD/月，但附加量不能超过原配：4GB 内存的机器最多再加 4GB。

这四条里的第 1 条和第 3 条，是大部分排名靠前的测评文章没有写清楚的部分。更多细节和实时库存，👉 [进绿云官网核对当前套餐条款](https://greencloudvps.com/billing/aff.php?aff=6679)。

## 机房与中国方向的实际体验

绿云的机房覆盖确实广，日本东京、大阪、新加坡、中国香港、越南、美西洛杉矶等都有节点，适合需要多地区部署的场景。但直接从中国大陆访问的话要分两种情况说：官方专门标注了 ISP/精品直连的优化套餐（如香港 Premium、东京 CN2）线路有针对性优化；普通低价套餐走的是标准国际 BGP 路由，晚高峰访问国内容易出现延迟上升和丢包。国内访问为主的应用，建议套一层 Cloudflare 之类的 CDN，或者前面挂一台中转机。

## GreenCloud VPS 和搬瓦工怎么选

这两家经常被放在一起比，其实定位差得比较远，按场景分更实际。搬瓦工（BandwagonHost）2004 年成立，主打中国优化线路，主力套餐 CN2 GIA-E 入门版是 1GB 内存 / 2 核 / 20GB SSD / 1TB 月流量 / 2.5Gbps 端口，$49.99/季或 $169.99/年起，电信、联通、移动三网走 CN2 GIA，晚高峰也不容易拥堵。绿云同量级的 Budget KVM 只要 $6–$10/月，机房选择多得多，但国内方向没有这种优化。

一句话的判断：**要稳定回国线路、业务是国内用户访问为主，搬瓦工 CN2 GIA-E 这类中国优化套餐是对的方向，贵得有理由；预算紧、跑海外业务、或者需要多地区分布式节点，绿云的性价比更突出。**两者也可以搭配：绿云放业务，搬瓦工做国内加速入口。

## 常见问题

**绿云有固定优惠码吗？** 基本没有。它的促销模式是定期闪购：每年 10 月周年庆和 11 月黑五会放出“配置翻倍”或“价格减半”的循环年付特价机，卖完即止；其招牌的 Storage 大盘机平时长期缺货，只在这些节点限量补货。想蹲特价，关注这两个时间窗口，比到处找优惠码靠谱。

**控制面板好用吗？** Linux 套餐用 SolusVM 或较新的 VirtFusion 面板，一键重装、rDNS、自动备份、快照、救援模式都有，Budget KVM 默认附带 1 个免费 Backup/Snapshot。Windows 套餐直接远程桌面连上就是完整管理员权限。

**工单支持到底靠不靠谱？** 日常问题响应在低价商家里算快的，官网口径是平均 9 分钟。但要记住 Unmanaged 的边界：母机宕机、网络不通他们会处理，你自己装的服务出问题得自己查。

## 按场景给结论

- 只需要跑一个轻量网站或小服务：Budget KVM 的 SSDKVM-1，$6/月，先用一个月验证线路。
- 要 Windows 远程桌面、用超过一个季度：SuperSaving Budget-1，$10/月给 2GB 内存，比普通版划算。
- 数据库、动态网站对性能敏感：等周年庆或黑五的 Ryzen/EPYC 特价年付机，平时不急可以蹲补货。
- 需要大容量备份仓库：Storage 系列，年付几十美元能到 TB 级，但只在节日限量放出。
- 国内用户访问为主、对晚高峰敏感：绿云的普通套餐满足不了，直接考虑 CN2 GIA 类的中国优化线路产品。

下单前最后确认两件事：选中的机房流量是不是 APAC 减半口径，以及套餐属不属于不退款范围。确认完就可以👉 [去绿云官网下单](https://greencloudvps.com/billing/aff.php?aff=6679)。
