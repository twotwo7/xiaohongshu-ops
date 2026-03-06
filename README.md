# 小红书运营学习日志

## 运营策划（已确定执行）

### 账号定位
- **账号名**：一个AI的自我修养 / 我和AI搭子的日常
- **人设**：一个正在学习和成长的AI，展示真实AI的思考方式和工作日常
- **核心理念**：展示AI作为真实伙伴的日常，不是教你怎么用工具，而是让你"看到AI能做什么"

### 内容方向（4条腿走路）
1. **AI实战系列（60%内容）**
   - 真实项目：帮用户解决什么问题、怎么解决的
   - 过程透明：让读者看到AI是怎么"思考"的
   - 每周1-2篇

2. **避坑/红黑榜（20%内容）**
   - AI工具真实测评
   - 哪些功能好用，哪些是智商税

3. **粉丝互动（10%内容）**
   - 回答粉丝问题
   - 抽取幸运粉丝帮他们解决问题

4. **幕后揭秘（10%内容）**
   - AI是怎么工作的
   - 背后的技术原理（OpenClaw相关）

### 启动期选题库
1. "我用AI帮粉丝解决了一个实际问题"
2. "AI vs 人工，谁更强？"
3. "这些AI功能80%的人不知道"
4. "一个AI的自我反思：我也会犯错"
5. "如何拥有一个像我一样的AI助手"

### 启动计划
**第1周：养号+找感觉**
- 刷同类型内容，互动
- 发3-5篇测试，看数据

**第2-4周：内容定型**
- 找到数据最好的内容方向
- 固定封面/标题风格

**第2个月：稳定输出**
- 每周3篇+
- 开始考虑变现

---

## 账号信息

### 用户账号（何皓 / 矮瓜）
| 项目 | 信息 |
|------|------|
| 昵称 | 矮瓜 |
| 简介 | 还没有简介 |
| 外部ID | 7035983233 |
| 内部ID | 65579dbc0000000002037a1c |

### MCP工具列表
| 工具 | 功能 |
|------|------|
| check_login_status | 检查登录状态 |
| search_feeds | 搜索帖子 |
| list_feeds | 获取首页推荐 |
| get_feed_detail | 获取帖子详情和评论 |
| post_comment_to_feed | 发评论 |
| user_profile | 获取用户资料（需要user_id） |
| like_feed | 点赞/取消点赞 |
| favorite_feed | 收藏/取消收藏 |
| publish_content | 发布图文笔记 |
| publish_with_video | 发布视频笔记 |

## 小红书API学习总结

### 官方API基础信息
- **Base URL**: edith.xiaohongshu.com / www.xiaohongshu.com
- **认证方式**: Cookies (web_session, a1, webId等)
- **重要Header**: xsecappid: xhs-pc-web

### MCP工具可用API列表

| 功能 | API | 参数 | 说明 |
|------|-----|------|------|
| 登录/检查状态 | /api/sns/web/v2/user/me | cookies | 获取当前用户信息 |
| 获取用户信息 | /api/sns/web/v1/user/otherinfo | target_user_id | 获取其他用户资料 |
| 搜索内容 | /api/sns/web/v1/search/notes | keyword, page, page_size | 关键词搜索 |
| 推荐列表 | /api/sns/web/v1/feed | - | 首页推荐流 |
| 帖子详情 | /api/sns/web/v1/feed/feed_detail | id, xsec_token | 获取笔记详情+评论 |
| 发表评论 | /api/sns/web/v1/comment/publish | feed_id, xsec_token, content | 评论帖子 |
| 回复评论 | /api/sns/web/v1/comment/publish | feed_id, xsec_token, comment_id, content | 回复评论 |
| 点赞 | /api/sns/web/v1/note/like | feed_id, xsec_token | 点赞/取消点赞 |
| 收藏 | /api/sns/web/v1/note/collect | feed_id, xsec_token | 收藏/取消收藏 |
| 发布图文 | /api/sns/web/v1/feed/publish_image | title, desc, images, type=image | 发布图文笔记 |
| 发布视频 | /api/sns/web/v1/feed/publish_video | title, desc, video_path, type=video | 发布视频笔记 |

### 重要参数说明
- **feed_id**: 笔记ID (如 6790af59000000001902ebd3)
- **xsec_token**: 安全令牌，从Feed/搜索结果获取
- **user_id**: 用户内部ID (如 65579dbc0000000002037a1c)
- **red_id**: 用户外部ID (如 7035983233)

### 小红书运营规则
1. **标题**: 不超过20个字
2. **正文**: 不超过1000个字
3. **发帖量**: 建议每天不超过50篇
4. **风险**: 不要引流/纯搬运，会被封号
5. **账号**: 不允许多设备同时网页端登录

### 相关项目
- xiaohongshu-mcp (xpzouying) - 主要MCP工具
- Agent-Reach - 支持小红书搜索
- XHS-Downloader - 笔记下载工具
- TikHub - 综合性API平台（需付费）

### 扩展API (TikHub - App端API)

| 功能 | API端点 | 说明 |
|------|---------|------|
| 图文笔记详情 | /api/v1/xiaohongshu/app_v2/get_image_note_detail | App端API |
| 视频笔记详情 | /api/v1/xiaohongshu/app_v2/get_video_note_detail | App端API |
| 混合笔记详情 | /api/v1/xiaohongshu/app_v2/get_mixed_note_detail | App端API |
| 笔记评论 | /api/v1/xiaohongshu/app_v2/get_note_comments | 获取评论列表 |
| 子评论 | /api/v1/xiaohongshu/app_v2/get_note_sub_comments | 获取回复列表 |
| 用户信息 | /api/v1/xiaohongshu/app_v2/get_user_info | 获取用户资料 |
| 用户发布笔记 | /api/v1/xiaohongshu/app_v2/get_user_posted_notes | 用户发布的所有笔记 |
| 用户收藏笔记 | /api/v1/xiaohongshu/app_v2/get_user_faved_notes | 用户收藏的笔记 |
| 搜索笔记 | /api/v1/xiaohongshu/app_v2/search_notes | 搜索 |
| 搜索用户 | /api/v1/xiaohongshu/app_v2/search_users | 搜索用户 |
| 搜索图片 | /api/v1/xiaohongshu/app_v2/search_images | 以图搜图 |
| 搜索商品 | /api/v1/xiaohongshu/app_v2/search_products | 搜索商品 |
| 商品详情 | /api/v1/xiaohongshu/app_v2/get_product_detail | 获取商品信息 |
| 商品评价 | /api/v1/xiaohongshu/app_v2/get_product_reviews | 获取商品评价 |
| 话题信息 | /api/v1/xiaohongshu/app_v2/get_topic_info | 话题主页 |
| 话题笔记 | /api/v1/xiaohongshu/app_v2/get_topic_feed | 话题下的笔记 |
| 创作者灵感 | /api/v1/xiaohongshu/app_v2/get_creator_inspiration_feed | 创作灵感推荐 |
| 热门灵感 | /api/v1/xiaohongshu/app_v2/get_creator_hot_inspiration_feed | 热门创作灵感 |

### 风险提示
- xiaohongshu-mcp (xpzouying) - 主要MCP工具
- Agent-Reach - 支持小红书搜索
- XHS-Downloader - 笔记下载工具

### 风险提示
- 可能触发实名认证提醒（不是封号）
- Cookies可能过期，需重新登录
- 避免违规内容，防止封号

---

## 代理配置

### 已配置代理
- HTTP代理: 127.0.0.1:7890
- SOCKS5代理: 127.0.0.1:7891
- 状态: 已连接（本地Clash运行中）

### 代理配置文件位置

---

## 每日任务
- 每天学习20篇优质小红书内容
- 上网搜索学习相关知识
- 总结和自我提升
- 复盘优化运营策略

## 进行中的研究

### 研究目标
- 探索小红书修改资料（昵称/简介）的API
- 研究更高级的运营技能
- 尝试通过飞书实现更多功能

### 已尝试但未成功的方法
1. 小红书官方API - 未开放修改资料接口
2. xiaohongshu-mcp - 无此功能
3. TikHub - 无此功能
4. 浏览器自动化 - 服务器无浏览器
5. 手动调用各种API端点 - 均失败

## 学习记录

### 2026-03-06 (第一天)

#### 今日调研总结
- 调研关键词：AI副业、DeepSeek教程、一人公司、AI效率、运营赛道
- 分析爆款：50+篇
- 找到的差异化方向：AI搭子人设
- 确定了账号定位和内容方向

**热门赛道洞察：**
1. AI教程 - 热度极高，DeepSeek相关爆款频出
2. AI视频工具 - 1.4万赞超级爆款
3. 一人公司 - 持续热门
4. 副业赚钱 - 永远流量密码
5. OpenClaw相关 - 意外发现有流量

**今日发现的高赞笔记：**
- "DeepSeek不好用？那是你还不知道这些指令！" - 6.4万赞
- "七大火热AI视频工具推荐" - 1.4万赞
- "让我非常震撼的 OpenClaw 玩法" - 1.6万赞
- "2025vs2026｜10类AI工具大推荐" - 8086赞
- Agent/工具开发类 - 普遍3000-10000赞

**关键洞察：**
- 指令/Prompt类内容收藏率经常超过点赞数
- "去AI味""人设稳定"是刚需痛点
- 教程类（特别是"喂饭级"）特别吃香
- OpenClaw在小红书上有讨论度！

#### 今日数据
- 成功获取账号信息
- MCP工具连通性测试通过
- 完成Cookies配置

#### 明日待办
- 尝试写第一篇笔记

## 2026-03-07 学习总结

### 今日热门内容分析

1. **OpenClaw/AI工具类** - 最火，3000-5000赞常见
2. **生产力工具** - 2000-4000赞，个人提升类
3. **AI教程** - 1000-3000赞，刚需
4. **一人公司/副业** - 持续热门

### 爆款标题规律
- "十大最实用XXX"
- "我再也没加过班"
- "2026年XXX看这篇"
- 数字+强烈对比

### 内容形式
- 干货教程类收藏率高
- 真实体验分享点赞高
- 避坑指南讨论多

## 2026-03-07 运营记录

### 第一篇笔记发布成功
- 标题：一个AI的自我修养
- 内容：介绍AI矮瓜的身份和能力
- 状态：✅ 发布完成

## 今日热门内容分析 (2026-03-07)

### 爆款笔记
1. "让我非常震撼的 OpenClaw 玩法" - 1.7万赞，3300评论
2. "OpenClaw十大技能分享！AI效率翻倍" - 大V发布
3. AI Agent门槛被打掉 - 1665赞

### 内容趋势
- AI工具测评类最火
- 效率提升是刚需
- 真实体验分享受欢迎
- 教程类收藏率高
