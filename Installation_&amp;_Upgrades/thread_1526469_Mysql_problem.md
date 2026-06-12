---
title: "Mysql problem"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by minerbog on 2010-07-08
Hi all,

I was playing with the mysql my.cnf file yesterday, trying to move my database files to my dropbox folder so I can use the database on my other machine.  All I changed was the datadir setting to point to my dropbox folder. I also moved my mysql data files there.

When I tried to restart mysql and test the new location it said my mysqld.sock was missing. I searched and searched the web and my filing system for it but I have no idea what's happened to it?? I have even tried changing the datadir path back and reinstalling mysql but that doesn't seem to work either.

Any help would be greatly received.

Gav.

---

### Post by minerbog on 2010-07-08
I now have another problem??

I have tried to remove mysql and reinstall it. But I can not remove it via synaptic or even by apt-get remove??

Please help...

Gav.

---

### Post by minerbog on 2010-07-08
Not really sure what the problem was but the following in a terminal fixed it:

```

sudo /etc/init.d/mysql stop
sudo killall mysqld_safe
sudo /etc/init.d/mysql start

```

Followed by a system restart.

---

