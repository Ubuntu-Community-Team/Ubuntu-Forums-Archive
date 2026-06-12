---
title: "imposible installing ubuntu 10.04"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by xuxo on 2010-05-06
Hello i have a HP pavilion with a nividia graphic card, when a try to install ubuntu 64 bits, a graphic error appears, ubuntu start (ln live mode) but is impossible recognize the desktop. so i must to kill the X.

I tried to solved by this way: at install screen press F6 and select nomodeset.

the graphic problem is eliminated but now the installer doesn't work.

I don't know what to do, i can't find any thing. I would like to know if there is a solution installing ubuntu in text mode o something like that, or what can i do for solve the graphic error.

I have a AMD 64 processor, and a Nvidia getforce 6150

thanks a lot if you could help me with this

---

### Post by utnubuuser on 2010-05-06
Is there still a safe-graphics mode under F4 or F6?

---

### Post by Syke on 2010-05-06
Try the alternate/text installer.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by xuxo on 2010-05-09
I tried with the text mode installer but i still have the same problem, after installing ubuntu, i reboot and the graphic mode sucks, is impossible to work. i am not very new in ubuntu, i used ubuntu since hardy and it is the first time that happen me some thing like this. 
Maybe im going to wait for the next build of ubuntu.

thanks
Karmic rules !!
(sorry for the english)

---

### Post by efflandt on 2010-05-09
If you want to add kernel boot parameters, use your favorite editor with sudo prefix to edit /etc/default grub

Just duplicate the line below, comment out the original line and edit the duplicated line.  Not even sure if splash does anything in 10.04 anyway, but not using splash may help too. 

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"
GRUB_CMDLINE_LINUX=""

The bottom line above is for (recovery) kernels in the grub menu.

Then **sudo update-grub**

---

### Post by Catharsis on 2010-05-09
> **efflandt said:**
> If you want to add kernel boot parameters, use your favorite editor with sudo prefix to edit /etc/default grub

Just duplicate the line below, comment out the original line and edit the duplicated line.  Not even sure if splash does anything in 10.04 anyway, but not using splash may help too. 

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"
GRUB_CMDLINE_LINUX=""

The bottom line above is for (recovery) kernels in the grub menu.

Then **sudo update-grub**

You can do the same as above through GRUB, although it won't save (so do the above once you get into your desktop).

1) Hold down Shift while you boot to get the grub menu.
2) Press 'e'. Then replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

I also suggest you try to install the proprietary nVidia drivers through System->Administration->Hardware Drivers once you get a desktop.

---

