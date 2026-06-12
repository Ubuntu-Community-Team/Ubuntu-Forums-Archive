---
title: "Change Permission on Files and Folder using CHMOD to 777"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-29
I am installing Simple Machine Forums on Ubuntu Desktop Dapper but I need to set Files and Directory permission using CHMOD to 777 how to do that?

Sample I have this files and folders:
/var/www/smf

All the files and folders under smf must have 777 CHMOD permission

---

### Post by lukew on 2006-09-29
Hi
There is a -R command for recursively go down directories.


I hopw this helps.

Luke

---

### Post by textguru on 2006-09-29
> **lukew said:**
> Hi
There is a -R command for recursively go down directories.


I hopw this helps.

Luke

cant get it. hope you can post the whole command. thanks for your understanding...

---

### Post by binbash on 2006-09-29
chmod 777 /var/www/smf -R

---

### Post by textguru on 2006-09-29
> **binbash said:**
> chmod 777 /var/www/smf -R

thanks for the reply. I already got it! Case close. ;)

---

