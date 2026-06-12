---
title: "I need some help formating my 2nd partition to Linux"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by Fajitas on 2006-09-10
Hey, I'm very new here, I just formated my computer to Linux, I had a second hard drive that was on Windows and still is, but I wanna get rid enterely of Windows, I've browsed those forums and I've seen that I can use gparted, I downloaded it using synaptic but it doesnt seems to work, I cant format my hard drive when I reboot it stills asks me if I want to run on windows or linux, it doesnt seems right. Can someone help me fix this. Thanks in advance, take care.

---

### Post by aysiu on 2006-09-10
To format a drive, it needs to be unmounted.

So in GParted, right-click the second drive and unmount it before you delete it and reformat it as something else.

To get Windows out of the boot menu, do ```
sudo nano -B /boot/grub/menu.lst
``` and delete its entry (Control-K). To save do Control-X, Y, Enter.

---

