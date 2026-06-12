---
title: "[SOLVED] backuppc password"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by rkulp on 2008-05-04
I am trying to configure BackupPC which I installed using apt-get. For some reason I can't find the password for the BackupPC User, backuppc. Is there a way to find it? I thought I had changed it during the install but what I thought was the password does not work. I really don't want to uninstall and reinstall if it is not necessary.:(

---

### Post by rkulp on 2008-05-05
Well, I upgraded to 3.1.0 and noted while running configure.pl that the _BACKUPPCUSER_ is defaulted to backuppc but there is never a reference to a password. Then in Step 7: Talking to BackupPC it instructs you to change to backupuser:  su _BACKUPPCUSER_ so I typed in:

su backuppc

and the system asks for the password. Stuck again.

---

### Post by rkulp on 2008-05-05
I solved it by backing up the /ect/backuppc directory and then doing a complete remove including all config files. That cleared the username and password. Then

apt-get install backuppc

got me to an install screen where the automatically generated password was provided. After install was complete, I changed it to a more desirable password.

---

### Post by Morons on 2008-05-26
> **rkulp said:**
> I am trying to configure BackupPC which I installed using apt-get. For some reason I can't find the password for the BackupPC User, backuppc. Is there a way to find it? I thought I had changed it during the install but what I thought was the password does not work. I really don't want to uninstall and reinstall if it is not necessary.:(

While Installing you missed the Message what your password is, Also the instructions in how to change it
Just do this:
```
htpasswd /etc/backuppc/htpasswd backuppc
```
Saved me an re-install!:lolflag:

---

