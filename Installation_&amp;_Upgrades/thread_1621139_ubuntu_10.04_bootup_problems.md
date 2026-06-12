---
title: "ubuntu 10.04 bootup problems"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by smvarner on 2010-11-13
[SIZE=4]Hi when trying to startup Ubuntu 10.04 the screen goes blank and says no signal. But there are three Ubuntu's to chose from. the middle one will boot-up and works all right. But for when it is starting up the screen flashes and comes back on. the top one doesn't work at all screen goes blank but the lights on tower stay on. the bottom one starts to boot but when it gets to the screen for your id and pass. it goes all blank but for a white line on the right side of the screen. this is on an old e-machine with a dual boot windows xp home. currently with 1g of ram and a 160gb hard drive split in two. with an AMD processor and ATI graphics on board. cant remember the numbers after that come after Ubuntu on the grub it is listed three times. how do you remove the other. let me know if you need more info.               [/SIZE]

---

### Post by mörgæs on 2010-11-15
Is this a problem with a new installation, or is it an older installation which all of a sudden does not boot?

---

### Post by smvarner on 2010-11-15
[SIZE=4]It is a new install started with 9.04 and upgraded up to 10.04 it will start if the printer and scanner is off. i did all the updates before upgrading the upgrades come from update manger.

[/SIZE]

---

### Post by dino99 on 2010-11-15
remove xorg.conf as now the kernel directly deal with X

sudo rm -f /etc/X11/xorg.conf

sudo update-usbids && sudo update-pciids

sudo dpkg --configure -phigh -a

---

### Post by smvarner on 2010-11-16
> **dino99 said:**
> remove xorg.conf as now the kernel directly deal with X

sudo rm -f /etc/X11/xorg.conf

sudo update-usbids && sudo update-pciids

sudo dpkg --configure -phigh -a

[SIZE=4]Hi do i enter that in to a terminal and what is xorg.conf thank you for you're help.  [/SIZE]

---

### Post by mörgæs on 2010-11-17
> **smvarner said:**
> Hi do i enter that in to a terminal
Yes

> **smvarner said:**
> what is xorg.conf

A file on the path /etc/X11/xorg.conf


By the way, I guess a quick googling for this kind of questions is faster for you than asking here.

---

