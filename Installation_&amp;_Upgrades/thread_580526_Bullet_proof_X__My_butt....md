---
title: "Bullet proof X?  My butt..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by brunjes on 2007-10-18
So where is a graphical display for me to work with when I use ATI and install 7.10 from scratch (no upgrade). I thought every type of hardware would get at least 800x600 resolution as a worst case?  No chance on my ATI X1400. Not even a usable terminal (via Ctrl-Alt-F1). Horrible!!!!

Good God, how hard can that be????

---

### Post by Pumalite on 2007-10-18
Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.
(it might very well work in Gutsy too)

---

