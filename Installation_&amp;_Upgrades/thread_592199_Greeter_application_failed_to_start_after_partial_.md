---
title: "Greeter application failed to start after partial upgrade"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by mikecomua on 2007-10-26
Hi, I had Ubuntu 7.04 and then I decided to upgrade to Gutsy. When the upgrade process stopped for a while I rebooted my machine and now i get a > Greeter application failed. Attempting to use another one message. Then I am left with a black screen and then a command prompt. THX:guitar:

---

### Post by koara on 2007-11-01
same here.. did you manage to fix it? any hints?

---

### Post by markharding557 on 2007-11-01
> **mikecomua said:**
> Hi, I had Ubuntu 7.04 and then I decided to upgrade to Gutsy. When the upgrade process stopped for a while I rebooted my machine and now i get a  message. Then I am left with a black screen and then a command prompt. THX:guitar:

I think the problem is the upgrade did not complete and needs to be finnished 
On the command line use sudo apt-get update followed by sudo apt-get dist-upgrade

---

### Post by lexarrow on 2007-11-02
My solution (as root) removing all xorg files and reconfiguring xorg.conf:

```
cd /etc/X11/
```
```
rm xorg*
```
```
dpkg-reconfigure xserver-xorg
```

here you have to choose the characteristics of your systems. It may be tough, but if you read the on-screen instructions it's quite simple. If you don't know what to fill in, the default it's usually ok.

hope it helps :)

---

