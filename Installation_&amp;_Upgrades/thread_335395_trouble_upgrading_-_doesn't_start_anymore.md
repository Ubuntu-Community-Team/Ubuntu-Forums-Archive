---
title: "trouble upgrading - doesn't start anymore"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by phberens on 2007-01-10
Hi there, 

I was quite happy with my Dapper Drake installation on the computer described below, but now there is some trouble after upgrading to Edgy Eft. 

When I boot, it shows the new redesigned boot screen, but without any text messages about what it is currently doing below (I am not sure whether this is normal, but in Dapper there was some text... *g*). Then, just before the progress bar indicates it finishes, it stops. There is a short flicker, like it is trying to start up the x server, and then there is just a green narrow bar across the display. Then the only option is to restart, as I haven't managed to get into the console yet, not with any key combination.

the laptop is a samsung x20 1860 with an ATI 128 MB graphics card. that was causing a bit of trouble when installing before, but we manually installed the ATI driver. 

has anybody similar experiences or hints? i would appreciate anything helpful!

best
Philipp

---

### Post by geek_Man on 2007-01-10
Well, I have zero experience with this. But, you might try booting into recovery mode and seeing if you can fix anything (again, I might be spouting nonsense), or you should back up everything you want to keep and install from an Edgy disc.

---

### Post by taurus on 2007-01-10
To see the boot message, edit /boot/grub/menu.lst and remove the word **quiet** from the kernel entry.

To reconfigure X again, boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
(Pick **vesa** as the driver for your graphic card...)
```

---

