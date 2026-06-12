---
title: "Installation problems..."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by captainkat07 on 2008-04-26
While upgrading, I encountered and error.  I was left with a system half Gutsy and half Hardy.  So I downloaded the ISO and decided I'd reinstall.  I had also just done this for a friend, so I can't figure out why it didn't work for me.  
I used gparted  on the live cd to delete my old Ubuntu partition and expanded my Windows partition to take its place.  Then, while trying to install and use the guided partition editor in the installer, installation crashed.  When I tried to run it again, it did not recognize my Windows Vista partition for what it was, so it did not give me the option to use the guided partition editor without overwriting the whole disk.  
Now, I can't boot into Windows to use the Windows partition manager, and I can't figure out how to make a new partition in gparted.  
I'm using the AMD64 version of 8.04.  
(I would just reinstall Windows, except I don't have a hard drive to back up stuff on.  Poor college student, you know...)
Any advice?
Thanks!!

---

### Post by Rocket2DMn on 2008-04-26
If it failed during the drive repartitioning, you might be in big trouble.  You can try booting from your windows cd and running the repair function.  You may need to enter the windows cd recovery console and run
```
fixmbr
```
You can also try the Super GRUB Disk to reset the MBR for windows or just fix/replace the current GRUB install with a working GRUB.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You may need to fiddle with the order I gave above (like try the repair function, fixmbr, that doesn't work, so try Super GRUB Disk, then Repair again...)

---

### Post by tamoneya on 2008-04-26
both of those solutions should work. I recommend the fixmbr one if you wish to get rid of windows and the supergrub one if you wish to dual boot.  Fixmbr will not work nicely with linux and will not add it to the boot record.  Grub will play nice with linux and windows and is recommended if you dual boot.

---

