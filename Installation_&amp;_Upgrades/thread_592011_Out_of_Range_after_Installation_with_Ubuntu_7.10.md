---
title: "Out of Range after Installation with Ubuntu 7.10"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Mjosch on 2007-10-26
Hi
I´m a totaly new to linux but I was able to install Ubuntu 7.10 on my Compute with the alternative CD becouse the live  CD would give me an out of range messege on my screen. So now I have a succsefully installed Ubuntu 7.10 but wen I try to start it the loadingscreen shows up and everything but after finishing the load process my screen goes black and says "Out of range". My spec:

Intel Pentium 2.8 Ghz
Geforce 6600 256mb

and I have a widescreen monitor with 1680X1050 resolution if that is the problem, becous the messege "Out of range" is from the screen.

Thank you in advance.

Sorry for my english, Swedish and Dyslectican.

---

### Post by taurus on 2007-10-26
Press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Mjosch on 2007-10-26
Thanx for the fast reply :), I´m going to try it out right away.

---

### Post by Mjosch on 2007-10-26
I don´t know what happend but I htink my problem just got bigger:(. I started Ubuntu normally and halfway into loading it just stopped and startded loading this in the console:

/dev/sda2 contains a file system withe errors, check forced
/dev/sda2 "loading"

so I let it load and then I come into console. So I login and try taurus way and write the code but it just says command culd not be found.
So I pressed <Ctrl> <alt> <del> and come to a window that says that it couldn´t start xserver. from here nothing works and I have to restart.

---

