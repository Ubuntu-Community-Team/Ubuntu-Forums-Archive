---
title: "How to install 10.10 alongside Win 7"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by PalapaGuy on 2010-12-27
New 64 bit Compaq laptop 250 GB with Win 7 pre-installed.  Using the Windows disk management tool I shrank the main partition creating 60 GB free space, which I then formatted as F:.  Now Windows reports the following partitions:

C:  157 GB capacity, 79% free
HP_TOOLS  99 MB capacity, 93% free
RECOVERY (D:  16 GB capacity, 14% free
SYSTEM  199 MB capacity, 83% free
UBUNTU (F:  60 GB, 100% free


OK, now moving right along to what the UBUNTU 10.10 64 bit live CD installer reports:

SDA1  1 MB  used, unknown contents
SDA2  208 MB  used, unknown contents
SDA3  169000 MB size, 3000 MB in use
SDA4  80000 MB size,  14000 MB in use

The installer does NOT offer the "alongside" installation option.  I also tried a 10.04 live CD installer, and it also did not offer the side-by-side option.

So neither installer can see Win7 on the disk.  Now how do I do the installation?  I'd like to dual-boot rather than devote the laptop to UBUNTU-only.

Help please.

---

### Post by karthick87 on 2010-12-27
Just delete an NTFS partition.And during ubuntu installation choose the option "Use free space" to install.

---

### Post by PalapaGuy on 2010-12-27
> **karthick87 said:**
> Just delete an NTFS partition.And during ubuntu installation choose the option "Use free space" to install.

That doesn't work for me.

Using the Win7 disk utility I deleted the F: partition (see above) thereby creating free space.  But I don't see free space using the 10.10 installer.  Installer gives me only two options: 1) Erase entire disk, or 2) Manual partitioning.  It does not offer use of free space or installing alongside existing O/S.

---

### Post by Quackers on 2010-12-27
Too late, I suspect.
If your original partitions were all Primary (and it is likely that they were), by creating a 5th partition without first deleting one, Windows has probably changed your partitions to "Dynamic Discs". These are useless to operating systems other than Windows. Ubuntu will not be able to install in them.
It is possible to change them back to basic but it will take some work. I can't get to my stored links at the moment so I can't give you a link. Google will help you find a way to do it.

---

### Post by Mark Phelps on 2010-12-27
> **PalapaGuy said:**
> That doesn't work for me....

Unfortunately, sometimes the advice you get here (as in use an installation option that no longer exists in the Ubuntu version you clearly specified) is worth exactly what you paid for it -- nothing.

The new installer (IMHO) is a real setback from the previous one in that:
1) They removed the most widely-used option for installing multiboot systems
2) They now force you into manual partitioning
... and ... worst of all ...
3) If you're not REALLY CAREFUL, you will end up accidentally reformatting your Windows partition, thereby, obliterating EVERYTHING there!

I've been installing Ubuntu systems for 4 years now, nearly always, in multi-boot environments, and this is the FIRST TIME I felt anxious about what the installer would do.

What I would suggest, if you're worried about your Win7 stuff, is to do the following:
1) Use the Win7 Backup feature to create and burn a Win7 Repair CD.  This can be used later to repair Win7 boot should that become corrupted during the dual-boot install
2) Download and install the Free version of Macrium Reflect.  Use this to image off a restoreable copy of your Win7 OS partition -- to an external drive or DVDs.
3) Use the boot disk option of Macrium Reflect to create their bootable Linux-based Recovery CD

At this point, with a restorable image of your Win7 OS, a CD for repairing Boot Loader problems, and a CD for restoring from that image.

So now, if you do accidentally reformat your Win7 OS partition (since this new installer goes out of its way to be confusing), you will have a way to get your working system back.

---

