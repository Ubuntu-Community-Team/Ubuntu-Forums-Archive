---
title: "Ubuntu 12.04.2 &amp; AMD Radeon HD 3000 Series Driver Support"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by hectorsales on 2013-07-05
Hi, I'm a little confused, I want to install ubuntu or xubuntu 12.04.2 my graphics card is AMD Radeon HD 3000 Series, the latest driver is AMD Catalyst ™ 13.1 Proprietary Linux x86 Display Driver according to the Description says:
"Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and[SIZE=3]** Kernel version up to 3.4"**[/SIZE]

In the release notes of "* buntu 12.04.2 LTS" says brings a new [SIZE=3]**Kernel 3.5.0-23.35.**[/SIZE] My question is my ATI/AMD driver supports "Ubuntu 12.04.2 LTS" ?.

Thanks...:o

---

### Post by Frogs Hair on 2013-07-05
hectorsales, I edited the title to reflect your question .

---

### Post by hectorsales on 2013-07-05
Ok, thanks...

---

### Post by Mark Phelps on 2013-07-06
Sorry to tell you this, but AMD has abandoned Linux driver support for the HD 2x/3x/4x series cards.  Starting with Ubuntu 12.04.2, the X-server version was upgraded such that it is incompatible with the AMD fglrx drivers.  With 12.04.2, all you can use now is the default open-source AMD drivers.

---

### Post by hectorsales on 2013-07-07
Thanks for the advice, I think I will use the default open-source AMD drivers.

:D

---

