## Выбор и настройка мониторинга в системе

### Мотивация

С тех пор, как бизнес начал предоставлять оформление заказов через API, данные Яндекс Метрики уже не дают полной картины. Чтобы начать улучшать систему, нужно внедрить мониторинг.

Внедрение мониторинга позволит:  
-  Быстрее отслеживать ошибки и устранять их.
-  Отслеживать быстродействие системы и распределение ресурсов.
-  Ускорение рабочего процесса и DevOps.
-  Повышение удовлетворённости пользователей.

### Выбор подхода к мониторингу

Система состоит из нескольких контейнеров (Internet Shop, Shop API, Shop DB, CRM, CRM API, MES, MES API, MES DB, Messages Queue, S3 storage).  

Будем использовать метод RED для мониторинга.

Показатели RED (Rate, Errors, Duration) обычно используются для мониторинга HTTP-трафика, а ещё они могут дать ценную информацию о производительности операций ввода-вывода (например, базы данных, вызовов внешних сервисов).

### Метрики и их назначение

Для начала будем собирать основные метрики для отслеживания общей производительности системы.  
Данные метрики позволяют выявить проблеммы с очередями сообщений, загруженность сервисов и критические ошибки, приводящие к возврату кода ошибки, а также загруженность БД.

1. Number of dead-letter-exchange letters in RabbitMQ.
2. Number of messages in flight in RabbitMQ.
3. Number of requests (RPS) for internet shop API
4. CPU % for shop API
5. Memory Utilisation for shop API
6. Memory Utilisation for shop db instance
7. Number of connections for shop db instance
8. Response time (latency) for shop API
9. Number of HTTP 200 for shop API
10. Number of HTTP 500 for shop API
11. Number of requests (RPS) for CRM API
12. CPU % for CRM API
13. Memory Utilisation for CRM API
14. Response time (latency) for CRM API
15. Number of HTTP 200 for CRM API
16. Number of HTTP 500 for CRM API
17. Number of requests (RPS) for MES API
18. CPU % for MES API
19. Memory Utilisation for MES API
20. Memory Utilisation for MES db instance
21. Number of connections for MES db instance
22. Response time (latency) for MES API
23. Number of HTTP 200 for MES API
24. Number of HTTP 500 for MES API

### План действий

1. Настроить инструмент Prometheus для сбора показателей.
2. Собрать RED-метрики для запросов сервиса, работы RabbitMQ и БД, производительности и отказов.
3. Настроить Grafana для визуализации показателей Prometheus.
