---
title: "grub loading error"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by eab912 on 2008-04-27
I am trying to install ubuntu on my desktop so that on one hd i have ubuntu and the other windows.  I have a amd 6400 processor, asus m2n sli deluxe mb and a nvidea 4000 video card.  When i try to start the computer after installation the message grub loading stage 1.5read error. does anyone know whats wrong.

---

### Post by Rallg on 2008-04-27
When you installed Hardy, where did you install Grub? Did you accept the default location for Grub, or did you use "Advanced" to place Grub elsewhere? My guess (it is only a guess) is that Grub is on the wrong partition, or that it points to files on the wrong partition.

If you have used Ubuntu (or any similar Linux) before, and know the basic of how the system works, you can insert boot from the CD into a live session, then inspect how the files were installed previously. In particular, you can see if /boot/grub is where you expect it to be, and whether /boot/grub/menu.lst contains what you think it should contain. Be sure that you are looking at folders and files on the hard drive, not on the live CD's virtual folder system.

---

