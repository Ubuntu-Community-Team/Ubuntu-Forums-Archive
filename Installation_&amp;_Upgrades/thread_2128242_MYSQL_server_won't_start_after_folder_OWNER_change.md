---
title: "MYSQL server won't start after folder OWNER change."
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by MaxTaylor on 2013-03-22
I'm running 12.04 with a LAMP installation. After successfully importing a huge database of information I got too curious and changed the "owner" of the /var/lib/mysql folder so I could look around. After realizing I should not have done that I changed the owner back to "root", or tried to anyway, but then phpadmin could not see the database or associated tables. In fact phpadmin would not even let me back in, probably for my own good. Ha.

Anyway, I re-started the machine thinking that would put me back where I started, but now mysql will not start at all. The status is "stop/waiting". 

My question is, does anyone know how I might put the mysql folder back to where it needs to be in the hopes that the server will start again?

The code I used to screw things up was this:

```
sudo chown martin /var/lib/mysql
```

I tried to change the owner back to root using:

```
sudo chown root /var/lib/mysql
```

Thanks.

---

### Post by feitingen on 2013-03-22
check /etc/passwd for the proper user.
The folder has to be owned by mysql or something.

---

### Post by darkod on 2013-03-22
Yeah, the original owner might not have been root at all. I'm not sure myself.

Try googling for the default owner of the folder (mysql installation) or similar.

And I guess I don't need to tell you know: linux is not windows, don't just start touching folder ownership and permissions unless you know what you need to change and that it will work. And as a minimum, you should have checked the original user/group ownership first so you know what to put back. Ownership and permissions are a big thing in linux.

---

### Post by prodigy_ on 2013-03-22
Easy way out: backup your DBs and configs (or, better yet, make a full backup) and then simply: ```
sudo apt-get purge mysql-server
sudo apt-get install mysql-server
```

---

### Post by MaxTaylor on 2013-03-22
Thanks for the suggestions all.

And thanks darkod. I do know permissions are a big deal in Linux. I just get over-confident sometimes and have to learn the hard way.

---

### Post by steeldriver on 2013-03-22
everything (including /var/lib/mysql/phpmyadmin) should be **mysql:mysql** afaik - at least that how it is on my 'play' server (I did an ls -R to confirm, and a 'find' for users / groups other than mysql - nada)

```

$ sudo ls -al /var/lib/mysql/
total 28700
drwx------  6 mysql mysql     4096 Mar 18 17:15 .
drwxr-xr-x 45 root  root      4096 Mar 17 18:07 ..
-rw-r--r--  1 mysql mysql        0 Mar 17 18:07 debian-5.5.flag
-rw-rw----  1 mysql mysql 18874368 Mar 18 17:14 ibdata1
-rw-rw----  1 mysql mysql  5242880 Mar 18 17:15 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 Jan 10 00:30 ib_logfile1
drwx------  2 mysql mysql     4096 Mar 17 18:07 mysql
-rw-rw----  1 mysql mysql        6 Jan 23 06:33 mysql_upgrade_info
drwx------  2 mysql mysql     4096 Mar 17 18:07 performance_schema
drwx------  2 mysql mysql     4096 Jan 24 16:05 phpmyadmin
drwx------  2 mysql mysql     4096 Jan 10 00:30 test
```

I don't think apt-get purge removes actual database files / dirs - just configs

---

### Post by MaxTaylor on 2013-03-22
I changed the owner back to mysql as listed in the my.cnf file, the server restarted and all seems to be back to normal.

THANK YOU all very much!

---

