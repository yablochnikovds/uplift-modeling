# Uplift Modeling: от простой к сложной

Образовательный проект по **uplift-моделированию** — одной из ключевых техник причинно-следственного машинного обучения (causal ML), используемой в маркетинге, медицине и продуктовой аналитике для оценки **индивидуального эффекта воздействия** (Individual Treatment Effect, ITE).

В одной Jupyter-тетрадке последовательно — от самой простой модели к самой сложной — реализованы **семь основных подходов** к uplift-моделированию. Каждая модель:

- выводится с нуля с подробным теоретическим объяснением;
- реализуется собственноручно на `numpy` / `scikit-learn`;
- сверяется с эталонной реализацией из `scikit-uplift` / `causalml`;
- применяется к одному и тому же реальному датасету (Hillstrom Email);
- обучается с тремя разными базовыми моделями: **LogisticRegression**, **RandomForest**, **CatBoost**;
- оценивается тремя стандартными uplift-метриками: **Uplift@k**, **Qini AUC**, **AUUC**.

В конце — единая таблица сравнения и визуализация Qini-кривых всех моделей.

## Содержание тетрадки

1. **Введение в uplift-моделирование** — что это, зачем нужно, четыре сегмента клиентов, формальное определение CATE/ITE, отличие от обычной классификации.
2. **Датасет Hillstrom Email** — реальные данные email-маркетинга (64 000 наблюдений), EDA, подготовка для бинарного uplift.
3. **Метрики качества** — Uplift@k, Qini-кривая, AUUC. Реализация с нуля + проверка на sklift.
4. **Семь моделей** (от простой к сложной):
   1. **S-Learner** (Solo / Single Model)
   2. **T-Learner** (Two Models)
   3. **Class Variable Transformation** (Jaskowski / Lai)
   4. **X-Learner** (Künzel et al., 2019)
   5. **R-Learner** (Nie & Wager, 2021)
   6. **DR-Learner** (Doubly Robust)
   7. **Causal Forest / Uplift Random Forest**
5. **Итоговое сравнение** — таблица всех моделей × всех базовых классификаторов × всех метрик; Qini-кривые на одном графике; рекомендации.

## Быстрый старт

```bash
# 1. Клонировать репозиторий
git clone https://github.com/yablochnikovds/uplift-modeling.git
cd uplift-modeling

# 2. Создать виртуальное окружение (рекомендуется)
python3 -m venv .venv
source .venv/bin/activate

# 3. Установить зависимости
pip install -r requirements.txt

# 4. Запустить Jupyter
jupyter notebook uplift_modeling.ipynb
```

Датасет Hillstrom скачивается автоматически при первом запуске (через `sklift.datasets.fetch_hillstrom`).

## Структура репозитория

```
.
├── README.md                  # этот файл
├── requirements.txt           # зависимости
├── uplift_modeling.ipynb      # основная тетрадка (запускается end-to-end)
├── LICENSE                    # MIT
└── .gitignore
```

## Для кого этот проект

- **Студентам и новичкам в ML** — пошаговое объяснение от 4 типов клиентов до доказательства состоятельности оценщика DR-Learner.
- **Дата-сайентистам** — готовый референс-код для production-задач: pipelines, метрики, сравнение бэйзлайнов.
- **Исследователям** — обзор современных meta-learners (Künzel, Nie–Wager, Athey) с воспроизводимыми экспериментами.

## Ключевые источники

- **Gutierrez & Gérardy (2017)** — *Causal Inference and Uplift Modeling: A Review of the Literature*
- **Künzel, Sekhon, Bickel & Yu (2019)** — *Metalearners for estimating heterogeneous treatment effects using machine learning*
- **Nie & Wager (2021)** — *Quasi-oracle estimation of heterogeneous treatment effects*
- **Athey & Imbens (2016)** — *Recursive partitioning for heterogeneous causal effects*
- **Jaskowski & Jaroszewicz (2012)** — *Uplift modeling for clinical trial data*
- **scikit-uplift** — https://www.uplift-modeling.com/
- **causalml** — https://causalml.readthedocs.io/

## Лицензия

[MIT](LICENSE)
