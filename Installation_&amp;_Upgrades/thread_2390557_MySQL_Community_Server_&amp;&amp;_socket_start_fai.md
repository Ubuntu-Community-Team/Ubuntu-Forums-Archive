---
title: "MySQL Community Server &amp;&amp; socket start failure"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by krvl on 2018-04-30
Hello,

[B]TL;DR
[/B]Everything seems in place, but mysql fails to start.

when
```

~$ sudo service mysql restart
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.

~$ systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since E 2018-04-30 11:19:00 EEST; 2min 0s ago
  Process: 1542 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)

apr   30 11:19:00 inverted-ping systemd[1]: Failed to start MySQL Community Server.
apr   30 11:19:00 inverted-ping systemd[1]: mysql.service: Unit entered failed state.
apr   30 11:19:00 inverted-ping systemd[1]: mysql.service: Failed with result 'exit-code'.
apr   30 11:19:00 inverted-ping systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
apr   30 11:19:00 inverted-ping systemd[1]: Stopped MySQL Community Server.
apr   30 11:19:00 inverted-ping systemd[1]: mysql.service: Start request repeated too quickly.
apr   30 11:19:00 inverted-ping systemd[1]: Failed to start MySQL Community Server.

```

After the error above /var/run/mysqld folder with it's contents is gone.
When re-creating the foldre and it's contents, mysqld_safe just exits
```

artur@inverted-ping:~$ sudo touch /var/run/mysqld/mysqld.sock
artur@inverted-ping:~$ sudo chown mysql:mysql /var/run/mysqld/*
artur@inverted-ping:~$ sudo mysqld_safe
2018-04-30T08:24:22.552847Z mysqld_safe Logging to syslog.
2018-04-30T08:24:22.556963Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2018-04-30T08:24:22.581488Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
2018-04-30T08:24:24.473120Z mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
artur@inverted-ping:~$ mysql -u root -p status
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysql.sock' (2)
artur@inverted-ping:~$ sudo ls -lah /var/run/mysqld/
total 0
drwxr-xr-x  2 root root  40 apr   30 11:24 .
drwxr-xr-x 31 root root 960 apr   30 11:23 ..

```

mysqld should be running

```

artur@inverted-ping:~$ ps -aux | grep mysql
artur     3619  0.0  0.0  17520  1120 pts/13   S+   11:27   0:00 grep --color=auto mysql
artur@inverted-ping:~$ ps -aux | grep mysqld
artur     3621  0.0  0.0  17520  1116 pts/13   S+   11:27   0:00 grep --color=auto mysqld

```

[my.cnf]("https://pastebin.com/VMDXa4GZ")

[/var/log/mysql/error.log]("https://pastebin.com/0hfkxHTS")

I've tried purging and reinstalling LAMP but mysql have failed to connect.

Ubuntu 16.04.4 LTS

I'm going in circles. Any help is appreciated!

---

### Post by krvl on 2018-05-09
Eventually upgraded to 18.04 and started logging changes I've made to the system to backtrack possible issues.

---

