---
title: "User and Password missing"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by Vonko on 2007-04-03
I did a new ubuntu install on a PC. After everything was running, including all upgrades, I had the bad idea to change the user name from 6 characters to only 1 (Example: from AAAAAA to only A). I never changed the password. Now I am unable to login and I tried everything I found, unsuccessfully. I get the typical message saying something to the effect "unrecognized user and password"
I want to first, access the root where the user/password exist and change it. I do not know if it is superuser or what, but is the main user that can do everything.
Please help, I really do not want to re-install everything.

---

### Post by taurus on 2007-04-03
Boot into recovery mode from GRUB menu and see what the username of your account now.

```
ls -la /home
```

---

### Post by Vonko on 2007-04-03
Thank you for your reply. I made some progress, I got to see this:

drwxr-xr-x   3  root root 4096 Apr 3  01:47
drwxr-xr-x 21  root root 4096 Apr 3  02:56
drwxr-xr-x 18  A (spaces)  AAAAAA  Apr 3  04:43  [COLOR="Blue"]AAAAAA[/COLOR]

note: ( ) are mine
Remember, I thought I changed the user name from AAAAAA to only A. Did I change a directory name instead? I still cannot access Ubuntu. The password seams to remain unchanged to what it was, this because on safe mode it asked me for it and the OS (unix) accepted it.

---

### Post by zvacet on 2007-04-03
In recovery mode type this
```
adduser AAAAAA admin
```
This will give superuser privileges and you will be able to login.After that go to the users &groups and make new users or correct old one.

---

