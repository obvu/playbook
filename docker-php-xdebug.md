# Настройка Xdebug в Docker для PHPStorm

В **Preferences > Languages & Frameworks > PHP** добавляе новый CLI Interpreter. Выбираем Docker Compose и PHPStorm автоматически найдет Xdebug:

![](https://github.com/obvu/playbook/blob/master/images/CLI-interpreter.png)

В **Preferences > Languages & Frameworks > PHP > Servers** 

![](https://github.com/obvu/playbook/blob/master/images/Server.png)

При этом в `docker-compose.yml` для контейнера backend нужно добавить 
```yml
    fpm:
      ...
      environment:
        XDEBUG_CONFIG: remote_host=${REMOTE_HOST}
        PHP_IDE_CONFIG: serverName=debug
```

и в `.env` файл 
```dosini
REMOTE_HOST=172.17.0.1
```
