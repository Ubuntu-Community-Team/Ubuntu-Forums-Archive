---
title: "Ubuntu install with 7.04 with live and alternate"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by ankur_gupta10 on 2007-10-08
I have an old machine p3 866 Mhz, 512 MB ram, 2HDD -20 and 40GB, Mercury 815 motherboard with onboard graphics card. 

Tried the live CD for installing Ubuntu 7.04 and after pressing enter to the default install on the main screen, the scren goes blank.

Also tried the alternate Kubuntu 7.04 CD and when trying to install got the following error. ATA 1.01:ATA revaliation failed(errno=-5). It then went ahead to use frame buffer and making me select keyboard settings etc, but then again the screen went blank..

Not to mention that i had earlier installed Ubuntu 6.06 on the same machine with no issues at all.

I am new to forums, apologies for anything missed. Any help is appreciated :-)

---

### Post by jnorthr on 2007-10-08
hi ankur
did your system work correctly under 6.06 ?  Do you have access to a partition editor like fdisk or gparted (you can get a copy here:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) ). It may be that your partitions are not correctly configured. You need to post a list of your partitions and your machine configuration if possible.

---

### Post by ankur_gupta10 on 2007-10-10
i tried with 6.06 again and could install it without any problems. So it seems that this is some problem with 7.04 than my system :)

How can i get my machine configuration. I would post the information. thanks

---

### Post by phr0ze on 2007-10-10
Boot the CD and once in it open your xorg.conf file. Change your display adapter to vesa, restart x and try the install.

hth

---

### Post by ankur_gupta10 on 2007-10-10
This is what happens when i try the ubuntu 7.04 live CD. I boot from it. Get the first screen where it presents you the bott option. I tried default, then tried with noapic, but nothing happens. then just there comes a cursor on the top left of my screen and nothing happens after that.

phr0ze, i do not know how to change the xorg.conf file.

---

