---
title: "Blank Screen in 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by nitrogen15 on 2011-10-14
During boot, I end up with a blank orange, purple or black screen.  I have an ATI 6850.  
I tried using this thread: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Hitting "e" while in GRUB didn't work, though.  Does this mean it's a kernel problem?  Also, when I tried following alternative instructions and hit Esc during a live-usb boot, I didn't get the GRUB menu.  Is there another good way to edit my config files and get this thing up and running?

---

### Post by collisionystm on 2011-10-14
> **nitrogen15 said:**
> During boot, I end up with a blank orange, purple or black screen.  I have an ATI 6850.  
I tried using this thread: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Hitting "e" while in GRUB didn't work, though.  Does this mean it's a kernel problem?  Also, when I tried following alternative instructions and hit Esc during a live-usb boot, I didn't get the GRUB menu.  Is there another good way to edit my config files and get this thing up and running?

Reboot your machine. Immediately after bios hold the shift key down. You will reach the grub menu.
Run system rescue
At the system rescue menu, hit resume normal boot and once again hold the shift key. Continue to hold until you hit the login prompt command line.

Login

sudo apt-get install fglrx

reboot.

---

### Post by nitrogen15 on 2011-10-14
Thanks!  This solved my problem.  A couple notes: I started safe mode from the BIOS rather than system rescue, but all other steps were the same.  Also, once FGLRX is installed I tried to install its suggested post-release update.  The update was broken, so I had to re-install FGLRX.  

While this driver works, boot-up is quite slow.  So give it a minute before deciding it's still broken.

---

