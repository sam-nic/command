# planfix-command

Универсальное микроприложение для отправки команды в callback webhook.

## Параметры URL

- `command` — команда
- `task` — ID/номер задачи
- `userEmail` — email пользователя
- `callback` — полный URL webhook, куда отправить данные

`callback` используется только как адрес назначения и не включается в JSON.

## Отправляемый JSON

```json
{
  "command": "...",
  "task": "...",
  "userEmail": "..."
}
```

После запуска приложение не показывает интерфейс:
1. читает параметры URL;
2. отправляет POST JSON на `callback`;
3. сразу вызывает `window.close()`.

## Пример

Если GitHub Pages опубликован как:

`https://sam-nic.github.io/planfix-command/`

вызов для Seppra:

`https://sam-nic.github.io/planfix-command/?command=test&task=26339&userEmail=user@example.com&callback=https%3A%2F%2Fseppra.planfix.ru%2Fwebhook%2Fjson%2Fcommand`

Важно: значение `callback` следует URL-кодировать, потому что сам callback может содержать `?`, `&` и другие специальные символы.
