---
title: "Dual boot removal problems"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by pete1983 on 2010-08-20
I have installed Ubuntu 10.04 & Linux Mint 9 on the same computer. I would like to remove mint 9 lxde and keep Ubuntu 10.04 the problem is pretty simple I don't like mint and love Ubuntu. Can anyone help thanks?

---

### Post by kukker32 on 2010-08-20
back up all important stuff..

then burn ubunru 9.10 or 10.04 iso file to a cd/dvd

boot from cd/dvd and under installation choose. "remove all previous systems and us ewhole disk" (or something similar) when you're in the partition manager part

---

### Post by phillw on 2010-08-20
> **pete1983 said:**
> I have installed Ubuntu 10.04 & Linux Mint 9 on the same computer. I would like to remove mint 9 lxde and keep Ubuntu 10.04 the problem is pretty simple I don't like mint and love Ubuntu. Can anyone help thanks?

In case you ever want to 'try' things out in the future, and also to make backing up 'your' stuff easier, I'd suggest you make a seperate /home partition, details for that can be found at [New /home](https://help.ubuntu.com/community/Partitioning/Home/Moving).

Regards,

Phill.
P.S. if you are still interested in lxde, there is a ubuntu variant called [Lubuntu](https://wiki.ubuntu.com/Lubuntu).

---

### Post by dagdeniz on 2010-08-20
You don't have to format the part with Ubuntu. 

To which distro belongs the grub2? If it belongs to Ubuntu, simply format the partition with Mint with the help of your live cd (with gparted), reboot, run "sudo update-grub" and you're done. Do whatever you want with the empty partition (like phillw suggested, you move your home files there using the manual he linked). 
If grub belongs to Mint, re-install grub in Ubuntu before applying the procedure above.

---

