# DevOps Lab 6 — Ansible roles + CI intro

**Демидов Матвей Александрович, ФИТ-1-2024 НМ**  
**Дисциплина:** Методы и инструменты DevOps  
**Лабораторная работа:** ЛР по лекции 6 (Ansible roles, CI intro)

---

## 1) Цель работы
Перевести настройку nginx на целевой VM в формат **Ansible Role** и запускать настройку через плейбук, который подключает роль.

---

## 2) Задание
- Создать роль (roles), вынести задачи установки/настройки nginx в `roles/<role_name>/tasks`
- Использовать роль в плейбуке
- Выполнить запуск в режиме `--check --diff` и реальный запуск
- Зафиксировать результаты (логи + скриншоты)

---

## 3) Стенд

| Узел | Роль | IP | SSH из Windows |
|---|---|---:|---|
| VM1 | Control Node (Ansible) | `10.0.2.15` | `ssh student@127.0.0.1 -p 2222` |
| VM2 | Managed Node (Nginx) | `10.0.2.16` | `ssh student@127.0.0.1 -p 2223` |

Проверка в браузере Windows: `http://127.0.0.1:8080`

---

## 4) Структура репозитория
- `src/`
  - `playbook.yml` — плейбук, подключающий роль
  - `inventory.ini` — инвентарь (VM2)
  - `ansible.cfg` — настройки Ansible
  - `roles/nginx/` — роль nginx (tasks + files)
- `check_diff.log` — запуск `--check --diff`
- `run.log` — реальный запуск
- `screenshots/` — скриншоты выполнения

---

## 5) Запуск (на VM1)
```bash
cd ~/DevOpsLab6/src
ansible-playbook playbook.yml --check --diff
ansible-playbook playbook.yml
```

---

## 6) Скриншоты
### 6.1 Check + diff (failed=0)
![](screenshots/01_check_diff.png)

### 6.2 Реальный запуск (failed=0) и задачи роли
![](screenshots/02_playbook_run.png)

### 6.3 Результат в браузере
![](screenshots/03_result_browser_or_curl.png)
