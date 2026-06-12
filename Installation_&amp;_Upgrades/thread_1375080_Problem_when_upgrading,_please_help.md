---
title: "Problem when upgrading, please help"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by alexdf990 on 2010-01-07
i have recently installed linux ubuntu and set it up, i was then promted to install updates (roughly 174). i did this, however once the updates had been downloaded, they continue to install then about halfway through it freezes, nothing happens and time does not fix this problem. 
I have restarted the laptop and 4 options appear, including recovery menu's, i have re-installed ubuntu as what i tried from that menu did not work. It has now happened again, is there a way i can avoid, or fix this problem?
thanks alex,

---

### Post by gordintoronto on 2010-01-07
More info, please.  What version?  Installed how?  (As the sole OS, in a dual-boot, from wubi, or under Virtualbox).  How much space did you allocate to it?  In one partition or more?  How much memory on your computer?

If you do a wubi install, the default amount of space for Ubuntu is too small in at least one version.  (I forget which one.)

---

### Post by kansasnoob on 2010-01-07
> **alexdf990 said:**
> i have recently installed linux ubuntu and set it up, i was then promted to install updates (roughly 174). i did this, however once the updates had been downloaded, they continue to install then about halfway through it freezes, nothing happens and time does not fix this problem. 
I have restarted the laptop and 4 options appear, including recovery menu's, i have re-installed ubuntu as what i tried from that menu did not work. It has now happened again, is there a way i can avoid, or fix this problem?
thanks alex,

If you can run the Live CD, that is choosing "Try without changes ...." from the initial boot menu go to Applications > Accessories > Terminal and copy-n-paste these commands:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo
```

```
free -m
```

Then copy-n-paste all of those results back here.

I rather suspect an Xorg issue but that hardware info will help.

---

