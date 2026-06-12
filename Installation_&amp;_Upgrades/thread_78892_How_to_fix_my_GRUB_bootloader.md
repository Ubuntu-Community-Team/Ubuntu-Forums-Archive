---
title: "How to fix my GRUB bootloader?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by Lancelot on 2005-10-19
I have a problem with ubuntu...

how to fix this..i have so many files on the hard drive..

GRUBloading stage 1.5.

GRUBloading, please wait...
Error 17

please help me..

---

### Post by manicka on 2005-10-19
This may help

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

### Post by skoal on 2005-10-19
1. Post back your partition information here and your /boot/grub/menu.lst file (wrapping them in code tags '#')

Basically, grub can't determine what filesystem type you have.  More than likely this means you have an NTFS partition as your first (and you are dual booting).

If that's the case...

2. Make sure you have something like this in /boot/grub/menu.lst:

```
title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1
```

\\//_

---

### Post by chronusdark on 2005-10-19
i just an hour ago had the same problem i just went into my cmos and changed my harddrives from auto to lba and it worked perfectly

---

### Post by leezer3 on 2005-10-19
You've hit the CHS vs. LBA bug. First, boot with your Windoze XP cd, and get to the recovery console. There run:
```
fixboot
fixmbr
```
Reboot, and Windoze should boot fine. Now, you need to re-install GRUB. To do this, follow these instructions:
> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
(Shamelessly lifted from the thread posted above :D )

Now, you should be good to go!

Changing the drive access mode to LBA in the BIOS will fix the symptons of this problem, but not the root cause- Windoze accesses the disk in a different way to Linux, using a load of little values in the partition table which Linux doesn't care about, and the installer has a bad habit of messing these up.

Cheers

-Leezer-

---

