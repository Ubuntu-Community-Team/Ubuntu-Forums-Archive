---
title: "kernel upgrade"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by d_xtremw on 2007-10-06
Hi everyone, I'm using 7.04(feisty) and I was just wondering if it would be possible to upgrade to the    gusty kernel through the update manager without changing my settings and programs. I have alot of things here and some specific settings which i dnt wanna change. Does anyone know if these programs and settings will be affected if i upgrade to gutsy thru the update manager

also, i found some useful sites with instructions on how to upgrade to the gutsy kernel, is the samea s upgrading to gutsy and again, will my settings be affected

---

### Post by PmDematagoda on 2007-10-06
Use this simple guide:-

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by PmDematagoda on 2007-10-06
It is less riskier to just upgrade the kernel than the whole system. If you upgrade the whole system then you must be prepared to face problems due to certain programs and functions being incompatible with the newly upgraded system.

---

### Post by d_xtremw on 2007-10-06
so i can upgrade the kernel and not have to worry about losing anything i have on my system right now??

---

### Post by PmDematagoda on 2007-10-06
I am using Gutsy's kernel right now and I didn't lose any data, so most probably yours will be the same.

---

### Post by d_xtremw on 2007-10-06
thanx alot. im going to try it out now. these are 2 of the sites i was gonna use but needed to know the answers to my questions earlier:

[http://www.justubuntu.com/install_2_6_22-10_ubuntu](http://www.justubuntu.com/install_2_6_22-10_ubuntu)

[http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html](http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html)

---

### Post by PmDematagoda on 2007-10-06
Both those two web pages give almost the same exact installation processes with the only differences being the different kernel versions.

---

### Post by d_xtremw on 2007-10-06
my sources list is empty. after adding the gutsy respositories i tried opening the sources list and its a blank file:S

---

### Post by walkerk on 2007-10-06
```
gksu gedit /etc/apt/sources.list
```

is it empty?

---

### Post by PmDematagoda on 2007-10-06
Are you sure you put the right name? the code is:-

```
sudo gedit /etc/apt/sources.list
```

---

### Post by d_xtremw on 2007-10-06
oh my badd. i missed out "apt" wow sorry about that :-$

---

### Post by Pumalite on 2007-10-06
gksudo gedit /etc/apt/sources.list

---

### Post by walkerk on 2007-10-06
> **d_xtremw said:**
> oh my badd. i missed out "apt" wow sorry about that :-$

minor detail :D

---

### Post by PmDematagoda on 2007-10-06
> **walkerk said:**
> minor detail :D

Yet even that can cause a full system error, so you have to be exceptionally careful when you do commands concerning the core of the system.

---

### Post by d_xtremw on 2007-10-06
ok i jus restarted with the upgraded kernel. hopefully this will fix all the problems i was having with my hibernate/suspend sequence. thanks everyone!!

---

