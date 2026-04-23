# Published banners — анонсы SimpleWorld

База всех финальных баннеров, которые реально ушли в посты/сторис. Черновики и промежуточные версии тут НЕ лежат — они в `../banners/` рядом.

## Что делать когда нужен новый баннер

1. **Смотри ближайший по смыслу анонс** ниже → берёшь его шаблон из `_templates/` как базу
2. **Источники правды** (никогда не выдумывай и не генерируй AI-копии):
   - Логотип SW: `assets/brand/avatar-dark.png` (квадрат) или `sw-logo-crop.png` (cropped глифы)
   - Алекс: `assets/characters/alex-v41c-black.jpg` (канон UAT, используется в onboarding/alex-task)
   - Мира: `assets/characters/mira-rect5-3-dark.jpg` (канон UAT)
   - City: `assets/banners/cities/city-fut-3b.jpg`
3. **Рендер HTML → PNG** через headless Chrome:
   ```bash
   cd assets && python3 -m http.server 8765 &
   "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --disable-gpu \
     --window-size=1200,675 --screenshot=out.png \
     "http://localhost:8765/banners/your-banner.html"
   ```
4. **Visual self-check** перед отдачей — открой PNG, проверь края/обрезку/баланс

## Анонсы

| Дата | Папка | Событие | Форматы | Языки |
|------|-------|---------|---------|-------|
| 2026-03-31 | `2026-03-31-p1/` | Первый анонс SimpleWorld (П1) | 1080×1080 пост, 1080×1920 story, 2160 hero | EN, RU |
| 2026-04-03 | `2026-04-03-p2/` | Второй анонс П2 (варианты размера текста) | 1080×1080 (regular/large/small) | EN, RU |
| 2026-04-13 | `2026-04-13-qa/` | Q&A пост от Сергея | Пост + bot-alex layout | EN, UA |
| 2026-04-15 | `2026-04-15-tapbot/` | Soft launch Simple Tap Bot (orange) | 1080×1080 | EN, ES, RU, UK |
| 2026-04-20 | `2026-04-20-launch/` | SW Soft Launch 20.04 (city + "Project launch") | 2160×2160 HD | EN, RU, UK |
| 2026-04-20 | `2026-04-20-sw-alex/` | SW + Alex (logo left, character right) | 1200×675 (OG/пост) | EN |

## Форматы и когда

| Формат | Размер | Где используется |
|--------|--------|------------------|
| OG / LinkedIn / Twitter post | 1200×630 или 1200×675 | Ссылки, посты |
| Instagram пост | 1080×1080 | IG feed, Telegram канал |
| Instagram story | 1080×1920 | IG/TG story |
| Hero / banner HD | 2160×1080 или больше | Landing, презентации |

## Шаблоны в `_templates/`

| Файл | Паттерн | Пример использования |
|------|---------|----------------------|
| `template-logo-alex-1200x675.html` | Лого слева + Алекс справа, 50/50, чёрный фон | 2026-04-20 |
| `template-logo-left-image-right.html` | Лого + любое изображение справа, с fade | 2026-04-13 (bot-alex) |
| `template-city-fullbleed-1080.html` | City fullbleed + logo + headline + дата | 2026-04-15 launch banners |

## Правила (не нарушать)

- **Не выдумывать текст** на баннерах — только утверждённый copy (`screen-map-v1-copy-v3.md`)
- **Не генерировать через AI** персонажей — брать канон из UAT (`SimpleWorld.Services/frontend/src/assets/characters/`)
- **Тёмный фон** — чёрный `#000` (style D131 Dark+Neon)
- **Gold accent** — `#FFB547` (glow, highlights у Алекса)
- **Gender-neutral** тексты, без запрещённых слов (`banned-words.yaml`)
