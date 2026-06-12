---
title: "GRUB after Messy Uninstall"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by blairbeckwith on 2007-03-03
I recently bought a new hard drive,  and am giving the one I currently use to a friend who wants nothing to do with Ubuntu.  I couldn't figure out how to uninstall Ubuntu from the hard drive, so I booted from the Live CD, and used The GNOME Partition Editor to delete the Ubuntu partitions and expand the Windows XP partition to full size.  After doing this and booting, it went to GRUB still and I got 'Error 22'.  I figured GRUB wouldn't even exist anymore once I deleted the Ubuntu partitions, so I'm a little bit confused?  Could anyone walk me through what I have to do step by step?

---

### Post by teaker1s on 2007-03-03
so you want to fix windows?
either super grub or xp recovery console "fixmbr"

---

### Post by blairbeckwith on 2007-03-03
how can I get to the recovery console?

---

### Post by wavesound on 2007-03-03
> **teaker1s said:**
> so you want to fix windows?
either super grub or xp recovery console "fixmbr"

Hi
Whats super grub?

Cheers
Bob

---

### Post by bulldog on 2007-03-03
Just reinstall XP and GRUB would be gone.
You can resize the partitions inside windows if you want,or use the gparted live cd before you install windows.

Just deleting your ubuntu doesn't delete GRUB,because it's located in the MBR of your hard disk.

---

### Post by bulldog on 2007-03-03
> **wavesound said:**
> Hi
Whats super grub?

Cheers
Bob

Take a look here to find out,
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by teaker1s on 2007-03-03
live boot graphical boot iso to fix grub/boot os's
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

if your just looking to repair xp then boot xp disc select recovery console and type

```
fixmbr
```

fdisk on a floppy should also do this

---

