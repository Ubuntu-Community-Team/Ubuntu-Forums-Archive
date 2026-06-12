---
title: "Grub won't start unless usb stick mounted from boot"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by tictacman on 2011-01-11
Hello,

Here's my situation.

Before: I had 2 os's ubuntu and windows installed on my system. Recently, I decided to install ubuntu to a flash drive.  All went well except grub was not installed to the flash drive, but appended the existing grub setup on my hard drive.

Now:  Even if I set the default system in grub as windows, or the original ubuntu install, my system will not boot unless the usb stick is plugged in.  I get message.  Error: grub rescue:

My ideal solution:  To stop grub searching for my flashdrive before loading the boot menu, and if possible to write grub to the flash stick.

---

### Post by dino99 on 2011-01-11
open /etc/fstab and look if you have an usb entry there, might need to remove or comment that entry, then update-grub again ( without the stick )

---

### Post by C.S.Cameron on 2011-01-11
Same situation:

[http://ubuntuforums.org/showthread.php?t=1664438](http://ubuntuforums.org/showthread.php?t=1664438)

---

### Post by tictacman on 2011-01-11
I couldn't find a usb entry in fstab.  I tried installing legacy grub and then running grub-update but that didn't work.  Then I scrounged around on the web for solutions.  One post suggested installing lilo.  I tried a command: lilo -m /dev/*** and now I don't have a bootloader at all.  It just automatically boots into windows.  

sorry, the link you mentioned is not the post I saw.  I will try it

---

