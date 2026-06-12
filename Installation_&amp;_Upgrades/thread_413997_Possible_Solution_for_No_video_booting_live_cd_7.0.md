---
title: "Possible Solution for: No video booting live cd 7.04 - seems to be with ati cards"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by KennyG3987 on 2007-04-19
I found this as a possible solution though it seems to be for ati cards.

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

I started in safe graphics mode then said no to looking at the logs when an error message came up.
Then typed in these commands minus the  "sudo depmon -a" and i am now installing it on my laptop.


Kenny

---

