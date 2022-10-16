# evernote-example

Набор скриптов для работы с Evernote API.

## Как установить

1. Клонировать репозиторий:

  ```shell
  git clone https://github.com/semellot/evernote-example
  ```

2. Создайте в этой папке виртуальное окружение на Python версии 2 и запустите его:

  ```shell
  python2 -m virtualenv virtualenv_name
  source virtualenv_name/bin/activate
  ```

3. Установить зависимости:

  ```shell
  pip install -r requirements.txt
  ```

4. Перед использованием необходимо получить ключ доступа и токен к Evernote API.

  `Consumer Key` и `Consumer Secret` можно получить по [ссылке](https://dev.evernote.com/).

  `Developer Token` сгенерировать [здесь](https://sandbox.evernote.com/api/DeveloperToken.action).

  Вам понадобятся блокноты и заметки в Evernote. GUID блокнотов можно узнать с помощью скрипта `list_notebooks.py`, для того чтобы его использовать эти переменные можно оставить пустыми.
  GUID заметки можно узнать на странице заметки Evernote в браузере из ссылки:
  
  ```
  https://sandbox.evernote.com/u/0/Home.action#n=[GUID]&s=s1&ses=4&sh=2&sds=2&
  ```
  
  Создайте файл `.env` с данными:

  ```dotenv
  EVERNOTE_CONSUMER_KEY=[Consumer Key]
  EVERNOTE_CONSUMER_SECRET=[Consumer Secret]
  EVERNOTE_PERSONAL_TOKEN=[Developer Token]
  JOURNAL_TEMPLATE_NOTE_GUID=[GUID заметки]
  JOURNAL_NOTEBOOK_GUID=[GUID блокнота]
  INBOX_NOTEBOOK_GUID=[GUID блокнота]
  ```

  
## list_notebooks.py

Выводит список блокнотов пользователя с их GUID.
```shell
% python list_notebooks.py
```

## dump_inbox.py

Выводит содержимое блокнота с GUID в переменной `INBOX_NOTEBOOK_GUID` - названия заметок с их содержимым. Количество заметок для вывода можно регулировать с помощью аргумента:

```shell
% python dump_inbox.py 10
```

## add_note2journal.py

Создаёт заметку, копируя заметку с GUID в переменной `JOURNAL_TEMPLATE_NOTE_GUID`. Заметка будет создана в блокноте с GUID в переменной `JOURNAL_NOTEBOOK_GUID`.

Можно указать дату создания новой заметки с помощью аргумента:

```shell
% python add_note2journal.py <ГГГГ-ММ-ДД>
```
