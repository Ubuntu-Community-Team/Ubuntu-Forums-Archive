---
title: "USB Boot support for 7.10 (Quick question)"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by Guardian-Mage on 2007-10-09
Ok, I had installed Ubuntu 7.10 on my USB hard drive a little while ago. I installed GRUB to /dev/sda which I believe is my boot sector of the USB hd. Now I have modified my boot priorities and it boots to the USB but only comes up with a GRUB command line, no menu.

 I did modify the GRUB list file, changing the bottom so Ubuntu was on device hd0, and windows on hd1, because GRUB is on the USB it thinks the usb is hd0. 

Should I go back and change hd0 to sd0, or sd1, or whatever, or are their other files for me to modify?

---

### Post by louieb on 2007-10-09
haven't done a usb install. But the fact that you get the grub> prompt but don't get the menu.  Sounds like it can't find the menu.lst file or there is something in it that grub says I can't use it. 
Hard to say. Might post your menu.lst file and device.map file. Both can be found in /boot/grub

---

