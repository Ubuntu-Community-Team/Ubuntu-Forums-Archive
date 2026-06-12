---
title: "MySQL won't start after update"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by taecha on 2008-11-11
After today's update, mysql does not start anymore returning the following error:

```
ERROR 2002 (HY000): Can't connect to local MySQL server 
through socket '/var/run/mysqld/mysqld.sock' (2)
```

Everything used to work fine before the update to mysql Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (i486) using readline 5.2.

I am running Ubuntu Hardy.

I am thankful for any help!

---

### Post by rrwo on 2008-11-11
I'm having the same problem!

---

### Post by rrwo on 2008-11-11
I'm able to start mysqld manually and then connect to the server. So it's probably not configured to start automatically.

---

### Post by taecha on 2008-11-11
I can not.

I guess it might have something to do with AppArmor since I receive the following error message when restarting it:

```
Reloading AppArmor profiles  Skipping profile /etc/apparmor.d/usr.sbin.mysqld~
: Warning.
```

I saw the same error message during the update process.

---

### Post by taecha on 2008-11-12
Oddly enough, the problem "disappeared" after reboot!

---

