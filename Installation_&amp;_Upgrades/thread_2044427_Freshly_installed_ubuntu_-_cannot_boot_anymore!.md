---
title: "Freshly installed ubuntu - cannot boot anymore!"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by tromanow on 2012-08-19
So I installed my ubuntu then a bunch software like ruby and mysql. Everything worked fine until I tried to reboot. I can no longer log in as myself, the administrator. I can only log in as guest. When I try logging in as myself he seems to let me in, the screen flips  to the text mode and then back to the login prompt. I know the password is correct because when I put in an invalid one I instantly get "invalid password". I tried logging in as guest and then sudo-ing but he won't let me sudo from guest. Help please!! Is there any way I can still recover my installation?

---

### Post by 2F4U on 2012-08-19
Can you get to a virtual console (Ctrl-Alt-F1)? If yes, try to login.

---

### Post by Bucky Ball on 2012-08-19
Welcome. What release and version, please. ;)

---

### Post by Bucky Ball on 2012-08-19
> **2F4U said:**
> Can you get to a virtual console (Ctrl-Alt-F1)? If yes, try to login.

You could attempt this by choosing the recovery kernel when you boot the machine (second on list), drop to a shell, login in the terminal, as suggested, then:

```
startx
```

---

### Post by tromanow on 2012-08-19
Thanks, Ctrl+Alt+F1 worked! My .profile was messed up...
Btw. it's Ubuntu 12.04.1 LTS.

---

### Post by Bucky Ball on 2012-08-19
Pleae mark thread as solved from thread tools to help others. ;)

---

