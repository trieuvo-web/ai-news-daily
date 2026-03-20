# 🤖 AI News Automation System

Hệ thống tự động thu thập, phân tích và lưu trữ tin tức AI từ nhiều nguồn.

## 🎯 Chức năng

- ⏰ **Lên lịch**: Chạy tự động mỗi 2 giờ (9:00, 11:00, 13:00, 15:00, 17:00, 19:00)
- 📡 **Thu thập**: Từ 8+ nguồn tin AI uy tín (Hacker News, TechCrunch, OpenAI Blog, 机器之心, v.v.)
- 🧹 **Xử lý**: Deduplicate, ranking, tạo summary
- 📊 **Phân tích**: Đánh giá độ quan trọng, phân loại chủ đề
- 📤 **Lưu trữ**: Push lên GitHub repo theo cấu trúc YYYY/MM/
- 📱 **Thông báo**: Gửi tóm tắt qua Telegram

## 📁 Cấu trúc thư mục

```
ai-news-automation/
├── ai-news-digest/          # Skill gốc
├── daily-news/              # Tin tức hàng ngày
├── reports/                 # Báo cáo phân tích (JSON)
├── github-repo/             # Local copy của GitHub repo
├── venv/                    # Python virtual environment
├── run_news_bot.py          # Script chính
├── cron-runner.sh           # Cron job wrapper
└── latest-summary.txt       # Tóm tắt mới nhất
```

## 🚀 GitHub Repository

**Repo**: https://github.com/trieuvo-web/ai-news-daily

Cấu trúc lưu trữ:
```
YYYY/
  MM/
    ai-news-YYYY-MM-DD-HHMM.md
LATEST.md                    # File mới nhất (cập nhật real-time)
README.md
```

## ⚙️ Quản lý Service (macOS)

### Kiểm tra trạng thái
```bash
launchctl list | grep com.openclaw.ai-news-bot
```

### Tắt tạm thờiservice
```bash
launchctl unload ~/Library/LaunchAgents/com.openclaw.ai-news-bot.plist
```

### Bật lại service
```bash
launchctl load ~/Library/LaunchAgents/com.openclaw.ai-news-bot.plist
```

### Chạy thủ công
```bash
cd ~/.openclaw/agents/opencode/workspace/ai-news-automation
source venv/bin/activate
python3 run_news_bot.py
```

## 📊 Log Files

- `cron.log` - Log chính
- `launchd.log` - Log từ launchd
- `launchd.error.log` - Error log

## 🔧 Cấu hình

### Thêm nguồn tin mới
Edit: `ai-news-digest/config/sources.json`

### Điều chỉnh thờigian
Edit: `~/Library/LaunchAgents/com.openclaw.ai-news-bot.plist`

### Đổi GitHub repo
Edit: `run_news_bot.py` - thay đổi `GITHUB_REPO`

## 📱 Telegram Integration

Tóm tắt tin tức được lưu tại `latest-summary.txt` sau mỗi lần chạy.

## 📝 Lịch sử

- **2026-03-20**: Khởi tạo hệ thống
- **Lịch chạy**: 9:00, 11:00, 13:00, 15:00, 17:00, 19:00 hàng ngày

---

## 🔗 Links

- GitHub Repo: https://github.com/trieuvo-web/ai-news-daily
- Skill Source: https://github.com/konatatech/ai-news-digest-skill
