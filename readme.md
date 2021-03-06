# Корпоративный блог

## Установка и запуск
- Устанавливаем виртуальныю машину ```vagrant up```
- Подключаемся к машине ```vagrant ssh``` и выполняем команды для БД:
    - ```CREATE DATABASE blog_portal;```
    - ```CREATE USER 'blog_portal_user'@'localhost' IDENTIFIED BY 'password';```
    - ```GRANT ALL PRIVILEGES ON * . * TO 'blog_portal_user'@'localhost';```
    - ```FLUSH PRIVILEGES;```
- Переходим в папку ~/code и выполняем команду ```php artisan command:refresh_base ```, что равносильно командам:
    - ```php artisan migrate```
    - ```php artisan db:seed```
- Компилируем стили и скрипты ```npm run dev```
- При необходимости запускаем тесты: 
    - ```phpunit```
    - ```php artisan dusk```

## Доступы
- Администратор
```
login: slavka20082008@yandex.ru
password: 123456
```
- Модератор
```
login: slavka20082008@gmail.com
password: 123456
```

## Описание

Приложение включает в себя
1) Модуль статей:
    - фильтр на главной (ajax)
    - возможность комментирования статей; редактирования и удаления для админов. Для хранения дерева комментариев используется технология "nested sets"
    - в административной части предусмотрено создание статей, создание категорий статей с неограниченной вложенностью (используется технология "materialized path")
2) Модуль слайдера
    - используется слайдер [swiper](http://idangero.us/swiper/)
    - загрузка слайдов в админке, возможность их сортировки
3) Модуль обратной связи
    - возможность оставить отзыв на публичной странице части
    - возможность ответить на отзыв в административной части, ответы хранятся в логах (/storage/logs)
4) Модуль пользователей 
    - реализованы "роли" : администратор, модератор, пользователь с разными уровнями доступа к административной части
    - возможность банить юзеров в административной части
5) Модуль парсинга 
    - загрузка файлов csv в административной части сайта, их временное хранение в БД
    - для проверки работы, есть тестовый файл - /resources/example_test.csv
6) Модуль настроек
    - Возможность добавлять произволные пары "ключ" - "значение" для дальнейшего использования. Реализовано в виде табличного редактора, с помощью [Vue.js](https://vuejs.org/)
7) Языковые версии приложения: русская и английская

Используемая версия laravel 5.6

## Используемые дополнительные модули
- [Forms and HTML](https://laravelcollective.com/docs/master/html)
- [Intervention Image](http://image.intervention.io/getting_started/installation)
- [Laravel Excel](https://laravel-excel.maatwebsite.nl/)