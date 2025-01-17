# My Favorite Films — Blog
Интерактивный блог.

Создан в рамках дипломной работы по теме: «Анализ и сравнение написания web-приложений с использованием разных фреймворков».

## Цель проекта
Разработать простое веб-приложение с использованием Django для сравнения с подобной разработкой на Flask и FastAPI.

## Обзор проекта
Веб-приложение на базе фреймворка Django, которое позволит:
* админстраторам вносить записи в базу данных;
* пользователям просматривать каталог полностью или фильтруя по категориям.

## Структура проекта
Проект включает в себя следующие ключевые компоненты:

### Домашняя страница
Здесь отображается список всех категорий, имеющихся в базе данных. Каждый пункт — это ссылка на страницу каталога фильмов,содержащая slug категории в динамическом URL для фильтрации.

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/main_page.jpg">

Рис. 1. Домашняя страница

### Страница каталога
Здесь отображаются карточки фильмов с информацией. В зависимости от параметров запроса, отображается весь каталог фильмов или с фильтрацией по категориям, а также меняется заголовок страницы.
Также на странице есть кнопка выбора фильтра со ссылками, содержащими параметры.

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/catalog.jpg">

Рис. 2. Страница полного каталога

#

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/catalog2.jpg">

Рис. 3. Страница каталога с отбором по категории при переходе с домашней страницы

#

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/catalog3.jpg">

Рис. 4. Страница каталога с отбором по категории из фильтра

#

### Панель администратора
Немаловажным для удобства внесения записей в базу данных является наличие панели администратора. Django предоставляет возможность автоматической генерации страниц администрирования с авторизацией и панелью, где можно добавить записи в базу данных, а также искать, сортировать и фильтровать уже имеющиеся данные.

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/adm_log_dj.jpg">

Рис. 5. Авторизация админстратора

#

Для заполнения поля `slug` добавлена функция автоматического заполнения по введенному названию. 

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/adm_categ_dj.jpg">

Рис. 6. Добавление категории

#

Поле `img_url`, на случай отсутствия ссылки, автоматически заполняется, загружая предустановленное изображение.

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/adm_film_dj.jpg">

Рис. 7. Добавление фильма

#

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/catalog4.jpg">

Рис. 8. Добавленный фильм с изображением по умолчанию

### СУБД (Database Management System)

Данный проект требует подключения СУБД для хранения данных. Он позволяет подключить любую СУБД. Так как в перспективе возможно значительное увеличение объема данных, использовалась клиент-серверная реляционная СУБД PostgreSQL.

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/dms_cat_dj.jpg">

Рис. 9. Таблица категорий в базе данных

#

<img src="https://github.com/nsazhi/My-Favorite-Films-Blog/blob/master/screenshorts/dms_fil_dj.jpg">

Рис. 9. Таблица фильмов в базе данных

### Шаблоны страниц
base.html — базовый шаблон, подключающий Bootstrap и статические файлы. Содержит навигационную панель и футер. На его основе пишутся остальные шаблоны.

main.html — домашняя страница, отображающая все категории, имеющиеся в базе данных.

films.html — страница каталога всех фильмов, имеющихся в базе данных. На ее основе пишется страница каталога отфильтрованных данных.

films_by_category.html — страница каталога фильмов с фильтром по категории из параметров запроса.

## Установка проекта
Создайте виртуальное окружение:

`python -m venv newvenv`

Активируйте его:

`newvenv\Scripts\activate`

Клонируйте [проект](https://github.com/nsazhi/Blog-My-Favorite-Films-Django/tree/master)

Установите модули из файла requirements.txt:

`pip install -r requirements.txt`

В пакет `mff_app/mff_app` добавьте файл `local_settings.py`:

`cd mff_app/mff_app`

`cd . > local_settings.py`

Добавьте в него ваши конфиденциальные данные:

`SECRET_KEY = 'ваш секретный ключ'

DEBUG = False

DATABASES = {
    'default': {
        * ваши данные подключения к базе данных * 
    }
}`

В файл `mff_app/mff_app/settings.py` добавьте:

`from .local_settings import *`
