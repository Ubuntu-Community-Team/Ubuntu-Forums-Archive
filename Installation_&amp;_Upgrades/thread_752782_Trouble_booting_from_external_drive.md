---
title: "Trouble booting from external drive"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by CPesyna on 2008-04-12
I recently installed Ubuntu 7.10 on an 80 GB Maxtor OneTouch USB drive. The installation process went without a hiccup thanks to some great guides I found on these forums, but there's one lingering issue...

So, Grub and Ubuntu are installed on the exteral drive, and my BIOS boot order is
1) USB device
2) CD/DVD
3) Internal hard drive

In theory, if the USB drive is plugged in, the machine should boot to Ubuntu, and if it isn't, Windows XP should load. Unfortunately, that doesn't quite happen. If I plug the drive in and turn on the computer, it loads Windows. If I then restart from within Windows, Ubuntu loads. If I restart from Ubuntu, Ubuntu loads. If I shut down from either, Windows loads. 

So it seems that, for some reason, BIOS isn't getting time to recognize the drive before going further down the boot order. To test this, I've tried booting with the drive plugged in, and a bootable CD in the drive. When I do this, it boots from the CD. 

Any ideas?

---

### Post by buntu_Geek on 2008-04-12
Since you have installed ubuntu on pendrive lastly... you must have the GRUB only n your pendrive... and that during installation the MBR is made to point to GRUB in your pen drive.... and hence you are unable to boot with out the pendrive....

Solution:
You might try to install grub on your HDD where you can have options for windows and Ubuntu(in pen drive) -- which when chosen will boot only if the pen drive is plugged in...else results in a GRUB error...

By this you can boot with out pen drive... 

Hope i didnt confuse you... :D

---

