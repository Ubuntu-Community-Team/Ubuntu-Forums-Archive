---
title: "want to know root password of my pc"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Luai on 2007-06-30
I've just install ubuntu 7 on my pc but I don't know what is the password of root user...
Thanks

---

### Post by icecruncher on 2007-06-30
you don't have one, yet
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) should help out
If you want root access to something
run it via sudo <app>

---

### Post by GeeZor on 2007-06-30
if i remember correctly, the root password has not yet been set upon installation.
To do so you need to set it yourself..

```
 sudo passwd root 
``` should do the trick.
you will be asked a password, which is YOUR password (for the sudo action) after which you will be asked to set the password for root.

Also this info should be in the documentation.

after setting the root password, you can su - to switch to the root user.

Let me know if things dont work out for you..

---

### Post by cddot on 2007-06-30
The password is the password you supplied during installation. If you have forgotten, then start in recovery mode which should bring you to the root# prompt. At the root prompt, type in "passwd" (without the quotes) to change the password.

---

