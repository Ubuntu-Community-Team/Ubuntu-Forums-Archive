---
title: "Problem Installing Fiesty on Gateway M285-E"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by ripps818 on 2007-04-26
I've been having trouble installing Ubuntu 7.04 on my Gateway M285-E convertible notebook with ATI Radeon 1400 Mobility. Whenever I try to boot up to desktop LiveCD, Xorg gives me a Vesa(0) and Screen(0) error, and won't allow me to boot into Gnome. I used to use Gentoo Linux a long time ago on my old desktop, but I've forgotten alot of things. I think I need to install FGLRX, but I don't know how to install it from the console in Ubuntu.

---

### Post by Nichod on 2007-07-03
Any luck on this?

---

### Post by nicholim on 2007-07-12
I am also having this problem.

---

### Post by Pumalite on 2007-07-12
Try Alternate Cd Text Mode:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by nicholim on 2007-07-14
Hahah damn, you beat me by 24 hours pumalite.
I was feeling all cool when I figured it out.

---

### Post by Pumalite on 2007-07-14
Glad you got it!

---

### Post by stanz on 2007-12-17
> **ripps818 said:**
> I've been having trouble installing Ubuntu 7.04 on my Gateway M285-E convertible notebook with ATI Radeon 1400 Mobility. Whenever I try to boot up to desktop LiveCD, Xorg gives me a Vesa(0) and Screen(0) error, and won't allow me to boot into Gnome.

I've been having the same trouble ~ with no progress. As anyone worked thru this?

---

### Post by Pumalite on 2007-12-17
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

---

### Post by stanz on 2007-12-18
Hey Pumalite...Thanks VERY much for the info!
I should have ~ but, didn't have time to search bugs...nor to get a hint of the info you passed.
Will try when time permits...as I jumped to 7.10.

---

### Post by Pumalite on 2007-12-18
You are welcome. Good luck!

---

### Post by stanz on 2008-03-31
Without time to work thru this -- I jumped to Gutsy and enjoy that it simply works!

:)

---

