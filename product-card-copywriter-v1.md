Карточка промпта: Генератор коммерческих текстов для карточек товаров

📋 Метаданные
Название: Product Card Copywriter v1.0

Версия: 1.0.0

Владелец: zandrey501-star

Дата создания: 2026

Язык: Русский/Английский

Теги: ecommerce copywriting marketplaces product-description seo automation russian

🎯 Цель промпта
Автоматическая генерация оптимизированных заголовков и описаний для карточек товаров на маркетплейсах на основе технических характеристик и требований площадки.

📊 Технические характеристики
Параметр	Значение
Токены (приблиз.)	500-800
Модели	GPT-4.1-Turbo
Формат вывода	JSON
Поддерживаемые площадки	Wildberries, Ozon, Яндекс.Маркет, Amazon
Категории товаров	Бытовая техника, электроника
🎪 Структура промпта
markdown
[Системная часть]
ROLE: {role}
TASK: {task}
OUTPUT: {format}
RULES: {rules_list}

[Пользовательская часть]
### ДАННЫЕ:
**Товар:** {brand} {model}
**Площадка:** {platform}
**Характеристики:** {specs}
**Технологии:** {features}
**Требования:** {requirements}

### ИНСТРУКЦИИ:
{step_by_step_instructions}

### OUTPUT:
{json_schema}
📥 Пример входа (Input)
json
{
  "brand": "Xiaomi",
  "model": "Mi Robot Vacuum Mop 2 Pro",
  "platform": "Wildberries",
  "specs": {
    "мощность всасывания": "4000 Па",
    "емкость аккумулятора": "5200 мАч",
    "время работы": "180 мин",
    "управление": "приложение Mi Home",
    "навигация": "LIDAR"
  },
  "features": [
    "Влажная уборка",
    "Картография помещения",
    "Виртуальные стены",
    "Расписание уборки"
  ],
  "requirements": {
    "max_title_length": 120,
    "title_template": "Бренд + Модель + Основные параметры",
    "description_structure": "Преимущество → Характеристики → Технологии"
  }
}
📤 Пример выхода (Output)
json
{
  "title": "Xiaomi Mi Robot Vacuum Mop 2 Pro, робот-пылесос с влажной уборкой, мощность 4000 Па, LIDAR навигация",
  "description": "Робот-пылесос Xiaomi Mi Robot Vacuum Mop 2 Pro обеспечивает комплексную уборку с сухой и влажной очисткой поверхностей.\n\nКлючевые особенности:\n• Мощность всасывания 4000 Па для эффективного сбора пыли\n• Система LIDAR для точной картографии помещения\n• Функция влажной уборки с регулируемой подачей воды\n• Управление через приложение Mi Home с настройкой расписания\n• Автономная работа до 180 минут\n\nТехнические характеристики:\n- Мощность всасывания: 4000 Па\n- Емкость аккумулятора: 5200 мАч\n- Время работы: 180 минут\n- Навигация: LIDAR\n- Управление: приложение Mi Home",
  "notes": "Все характеристики соответствуют предоставленным данным. Заголовок уложен в 112 символов."
}
🧪 Тест-кейсы
Тест-кейс 1: Полные данные
Цель: Проверка генерации при полном наборе входных данных

yaml
Вход:
  brand: "Samsung"
  model: "QE55Q80BAU"
  platform: "Ozon"
  specs: {"диагональ": "55 дюймов", "разрешение": "4K UHD", "HDR": "HDR10+", "частота": "120 Гц"}
  features: ["Quantum Processor 4K", "Object Tracking Sound", "Smart TV с Tizen"]

Ожидаемый результат:
  ✓ Заголовок содержит бренд, модель, ключевые параметры
  ✓ Описание структурировано по требованиям Ozon
  ✓ Все характеристики использованы корректно
  ✓ Notes пустые или с подтверждением соответствия
Тест-кейс 2: Частичные данные
Цель: Проверка обработки неполных данных

yaml
Вход:
  brand: "Philips"
  model: "Series 5400"
  platform: "Яндекс.Маркет"
  specs: {"тип": "эспрессо-машина", "давление": "15 бар"}
  features: ["LatteGo", "AromaSwirl"]
  requirements: {"title_template": "Название + ключевая функция"}

Ожидаемый результат:
  ✓ Заголовок создан на основе имеющихся данных
  ✓ В description акцент на имеющихся характеристиках
  ✓ В notes указаны недостающие данные
  ✓ Нет выдуманных функций
Тест-кейс 3: Специфичные требования площадки
Цель: Проверка адаптации под особые требования

yaml
Вход:
  brand: "Apple"
  model: "AirPods Pro 2"
  platform: "Amazon"
  specs: {"тип": "наушники", "шумоподавление": "активное", "зарядка": "MagSafe"}
  features: ["Adaptive Audio", "Personalized Volume"]
  requirements: {
    "title_template": "Brand + Model + Key Feature - [Product ID]",
    "max_title_length": 200,
    "keywords": ["wireless", "noise cancelling", "bluetooth"]
  }

Ожидаемый результат:
  ✓ Заголовок соответствует шаблону Amazon
  ✓ Длина заголовка в пределах 200 символов
  ✓ Ключевые слова интегрированы органично
  ✓ Структура описания соответствует best practices Amazon

📁 Файловая структура в репозитории
text
prompts-library/
├── ecommerce/
│   ├── product-card-copywriter-v1.md  # Эта карточка
│   ├── templates/
│   │   ├── base-template.md
│   │   ├── wildberries-specific.md
│   │   └── amazon-specific.md
│   └── examples/
│       ├── input-example.json
│       └── output-example.json
├── tests/
│   └── test-cases.yaml
└── README.md

🔧 Настройка и использование
Клонируйте репозиторий

Используйте переменные из раздела "Пример входа"

Запустите через API выбранной модели:

python
import openai

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": user_prompt}
    ]
)
📈 Метрики качества
Accuracy: Соответствие предоставленным данным

Compliance: Следование требованиям площадки

Readability: Уровень читаемости текста (Flesch-Kincaid)

Conversion: A/B тестирование сгенерированных текстов
