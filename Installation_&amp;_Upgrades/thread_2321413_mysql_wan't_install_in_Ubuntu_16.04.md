---
title: "mysql wan't install in Ubuntu 16.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by byo2 on 2016-04-22
I upgraded Ubuntu 15.10 to 16.04. Mysql failed to upgrade. I uninstall it but also a new installation give me errors:
```

> sudo apt install mysql-server mysql-client

[..]
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: errore nell'elaborare il pacchetto mysql-server-5.7 (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
                                                                                                             dpkg: problemi con le dipendenze impediscono la configurazione di mysql-server:
 mysql-server dipende da mysql-server-5.7; comunque:
  Il pacchetto mysql-server-5.7 non è ancora configurato.   (mysql-server-5.7 it is not configurred)

dpkg: errore nell'elaborare il pacchetto mysql-server (--configure):
 problemi con le dipendenze - lasciato non configurato
Elaborazione dei trigger per systemd (229-4ubuntu4)...
Elaborazione dei trigger per ureadahead (0.100.0-19)...
Si sono verificati degli errori nell'elaborazione:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I did:
```

sudo apt remove --purge mysql-server-5.5
sudo apt remove --purge mysql-server-5.6
sudo apt remove --purge mysql-server-5.7
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt update
sudo apt upgrade
sudo apt install mysql-server mysql-client

```

---

### Post by yancek on 2016-04-22
You need to use "sudo apt-get...." in the commands not just "sudo apt..." which you use in some of the commands.

---

### Post by byo2 on 2016-04-22
> **yancek said:**
> You need to use "sudo apt-get...." in the commands not just "sudo apt..." which you use in some of the commands.

Tryed also with apt-get in all, it did not work

Also tryed to uninstall mysql-common and dbconfig-mysql:
```

sudo apt-get remove --purge mysql-common mysql-client mysql-server dbconfig-mysql

```
and reinstall (after autoremove/autoclean/update/upgrade):
```

sudo apt-get install mysql-server mysql-client mysql-common dbconfig-mysql

```

Nothing changed..
Seem a bug:
[https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279](https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279)

The problem is that I really need mysql...

---

### Post by Maheriano on 2016-04-22
I had the same issue and just fixed it after spending 6 hours on it this morning.

If you check your MySQL error logs, you'll see the following lines:

2016-04-22T20:10:39.032812Z 0 [ERROR] unknown variable 'key_buffer=16M'
2016-04-22T20:13:16.767742Z 0 [ERROR] unknown variable 'myisam-recover=BACKUP'

Go into your MySQL configuration file:
> sudo nano /etc/mysql/my.cnf
and edit the lines containing those variables by placing a "#" in front of them so they look like these lines:

#myisam-recover         = BACKUP
#key_buffer             = 16M

Now continue the upgrade by running:
> sudo apt-get -f install
and it will continue installing MySQL.

---

### Post by byo2 on 2016-04-24
I uninstalled apache, mysql, php and various modules, deleted all configuration and old files, reinstalled, installed dbconfig-mysql after mysql and all worked fine.

Thanks to all :)

---

### Post by bretcb on 2016-04-24
> **Maheriano said:**
> edit the lines containing those variables by placing a "#" in front of them so they look like these lines:

#myisam-recover         = BACKUP
#key_buffer             = 16M


You just saved me 6+ hours, too.  Thank you so much!

---

### Post by micucci on 2016-04-25
> **bretcb said:**
> You just saved me 6+ hours, too.  Thank you so much!
...and 6 hours more for me ! Thanxxx a lot !

---

### Post by BFrere on 2016-04-28
> **Maheriano said:**
> I had the same issue and just fixed it after spending 6 hours on it this morning.

If you check your MySQL error logs, you'll see the following lines:

2016-04-22T20:10:39.032812Z 0 [ERROR] unknown variable 'key_buffer=16M'
2016-04-22T20:13:16.767742Z 0 [ERROR] unknown variable 'myisam-recover=BACKUP'
Didn't solved my issue, despite I had exactly the same symptoms.
In my case (upgrade from 14.04 to 16.04 LTS), the problem was that 

[FONT=courier new]# mysqld --initialize[/FONT]

command, which is part of the installation process, failed because the default data repository directory (/var/lib/mysql) was not empty. However, I ran "apt-get purges" just before...
Actually, there is a file remaining in this directory: [FONT=courier new]/var/lib/mysql/debian-5.7.flag[/FONT]
Just delete it:
[FONT=courier new]
sudo rm /var/lib/mysql/debian-5.7.flag [/FONT]

And run manually the initialisation process:
The database started then for me ("service mysql start")

Yours[FONT=courier new]
[/FONT]

---

### Post by kevpatts2 on 2016-07-05
```
sudo sed -i "s/key_buffer/key_buffer_size/g" /etc/mysql/my.cnf
sudo sed -i "s/myisam-recover/myisam-recover-options/g" /etc/mysql/my.cnf
```
This fixed it for me.

---

### Post by ernestorumo on 2016-08-08
This solved my problem too, you saved me a lot of time. Thanks

---

