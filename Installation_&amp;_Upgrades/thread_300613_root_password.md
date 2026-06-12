---
title: "root password?"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2006-11-15
firstly, you should know that i am a newbie.

now the question:
i have installed ubuntu on my PC. during the installation it asked to build an account and password for it. I named it freeuser. now when i try to login as root (in the recovery mode for eg.), and i enter the password for the free user account it show the wrong password error. please help me out here.
what is the password for root user.

---

### Post by taurus on 2006-11-15
If you boot your machine into recovery mode, you already log in as root so no need to use any password.  In fact, I don't even think you have to issue any password in recovery mode!!!  And if you want to run something as root when you log into freeuser, then use the sudo command...

---

### Post by dweez on 2006-11-15
In a normal boot (i.e., non-recovery mode), logging in as root is disabled.  This is a security feature and honestly should not be circumvented.  Anything you need to do can be done with sudo.  If you seriously need root access for something, you can log in normally (with u:freeuser, p:<what you set>) and do a su -s and give your sudo (i.e., the u:freeuser) password).  This will give you a terminal with root access.

---

