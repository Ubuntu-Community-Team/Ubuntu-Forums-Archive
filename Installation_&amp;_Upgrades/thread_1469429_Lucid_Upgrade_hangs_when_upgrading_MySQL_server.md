---
title: "Lucid Upgrade hangs when upgrading MySQL server"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by jamespi on 2010-05-02
When this happens you have to open a terminal, get the process id for mysql-server-5 then kill that process. Like this:

```
ps -A

```
then from the list of processes that it spits out look at the process id (the number at the beginning of the line) for mysql-server-5.

now type 

```
sudo kill -9 XXXXX
```

where XXXXX is the process id for mysql-server, and enter your password.

the upgrade process should now resume.

---

### Post by Hellola on 2010-07-14
Thank you, took me several installs / uninstalls

---

