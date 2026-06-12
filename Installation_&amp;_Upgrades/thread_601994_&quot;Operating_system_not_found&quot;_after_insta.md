---
title: "&quot;Operating system not found&quot; after installing Kubuntu"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by faberoo on 2007-11-03
Hello:
I've reformatted a hard disk and installed Kubuntu from the liveCD. I've told it to reformat my entire disk, and used the 'Use entire disk' option for partitioning. Everything went smoothly. When I rebooted, I got the dreaded "Operating system not found" error. I don't have any other drives or systems installed. Did Ubuntu not rewrite my MBR? When I enter my BIOS setup, my computer recognizes my drive as "Secondary Slave" - does this affect anything? I took out my Master drive for this installating. What went wrong with GRUB?

Thanks a lot!

---

### Post by perlluver on 2007-11-03
It should recognize the hard drive as master in bios.  Otherwise it will not boot up, I am pretty sure.

---

### Post by faberoo on 2007-11-03
It would not boot even if the partition is bootable and it's the only drive installed?

---

### Post by perlluver on 2007-11-03
> **faberoo said:**
> It would not boot even if the partition is bootable and it's the only drive installed?

Are the jumpers set to slave or master?  If they are set to slave it will not boot from it.

---

### Post by faberoo on 2007-11-03
Yes, it's set to slave - I'm doing a dual boot with my master drive. Why would it not boot the slave drive without the master drive, if I tell it to boot from it? Isn't that what happens when I dual boot? I'm confused, or maybe I just don't understand, sorry!

---

### Post by perlluver on 2007-11-03
If you are booting with both hard drives, then you have to select in bios to load from the second hard drive.  If you only have one hard drive in there, the slave then it has to be set to master otherwise it will not boot it.  If both hard drives are plugged in then you can try to boot the slave from BIOS.  Not sure it will work though.

---

### Post by faberoo on 2007-11-03
Well, what would you do for a dual boot on two drives to make it work? One must be set to master, the other slave!

Thanks

---

### Post by perlluver on 2007-11-03
Try this thread, see if it helps:  [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

