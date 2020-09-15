## tankiproxy
Простой proxy-сервер на основе Nginx-1.18 для устранения утечки памяти Танках Онлайн, путем замены .webp изображений на аналогичные более низкого разрешения

## Начало работы
Скачать и распаковать архив в любую директорию, выполнить скрипт `openssl-create.sh`, предварительно модифицировав файлы конфигурации `openssl-ca.cnf` и `openssl-server.cnf` нужным образом (по умолчанию нужно изменить параметр _commonName_default_ на любое значение)

После выполнения скрипта импортировать файл `cacert.pem` в раздел Доверенных центров сертификации Windows (для удобства имеет смысл изменить расширение файла на _.crt_)

Указать в файле `hosts` (по пути %windir%\System32\drivers\etc\) для хостов танков локальные ip-адреса:
```
127.0.0.1 tankionline.com
127.0.0.1 s.eu.tankionline.com
```
Запустить `nginx.exe` из корня директории, проверить работоспособность клиента игры (по умолчанию загрузочный фон будет уменьшенным в 4 раза)

## Как заменить текстуры
Готовый proxy-сервер можно использовать для записи имен всех загружаемых игрой ресурсов в файл логов `access.log`, после чего выбрать, загрузить и модифицировать нужные по своему усмотрению

Модифицированные ресурсы расположить в папке `www/` в соответствующей поддиректории, очистить кэш клиента/браузера, начать играть

### Примечания
+ При уменьшении текстур атласов карт `atlasN.webp` и анимированных красок `image.webp` необходимо также изменить их родственные файлы описания `atlases.json` и `frame.json`, прописав в них все числовые значения уменьшенные на такой же коэффициент что был выбран при уменьшении изображений. В противном случае можно получить недвигающиеся анимированные краски и черные карты в игре.
