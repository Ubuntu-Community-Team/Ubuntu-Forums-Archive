---
title: "OK to resize Win XP partition for dual-boot?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2009-12-13
I'm helping a Windows XP Home user transition to Ubuntu.  She wants to dual-boot Win and Ubuntu as there are some programs that are Windows-only (haven't explored the WINE options yet).

Will Windows XP get broken if I resize the partition it's on?  The target machine has a 60 GB hard drive which is all one large, NTFS partition where Win XP Home is installed.  I don't want to break her Win XP install somehow.  I realize in theory XP should not get broken by a mere partition resize, but I'm hesitant to do so, having never actually tried it.

I guess the other option is to do a Wubi install, since that doesn't require messing with the disk partitioning.

---

### Post by darkod on 2009-12-13
Yes, wubi is an option. And XP shouldn't get damaged by the resize but be sure to backup before starting, any partition handling has some degree of risk. For XP personally I prefer to boot with the ubuntu cd, Try Ubuntu option, and open Gparted (in System-Administration). You can resize your XP partition there.
VERY IMPORTANT: Just resize the XP partition and do nothing else. No need to create partitions for linux in advance. Boot XP few times and let it to the disk checks, it needs to "figure out" the resize. After you have booted it few times and you're sure it's happy with it, boot again with ubuntu cd, select Install Ubuntu, and let it Use Largest Available Free space (in other words the unallocated space created by the shrink). That should work out fine.

---

### Post by Objekt on 2009-12-13
Thanks.  In the meantime, I realized a normal, partitioned install is indicated for the user in question.  She has a notebook, and since Wubi apparently doesn't handle hibernation, it would not be the best option.

---

### Post by presence1960 on 2009-12-13
> **Objekt said:**
> Thanks.  In the meantime, I realized a normal, partitioned install is indicated for the user in question.  She has a notebook, and since Wubi apparently doesn't handle hibernation, it would not be the best option.

First defrag windows at least once or twice. 

Back up all data you don't want to lose.

Turn off System Restore in Control Panel until after Windows is resized. I would even get rid of page file until windows is resized.

Then use gparted Live CD or gparted from Ubuntu Live CD to resize windows.

---

### Post by Objekt on 2009-12-15
Done.  No problems at all.  Resizing the partition went way faster than I expected.  Though it is a very old, slow computer by today's standards (Dell Inspiron 8600 w/Intel Centrino 1.4 GHz single-core CPU), the HDD is only 60 GB.  The last time I resized a partition, it was on a 1 TB HDD and though with a much more powerful CPU (Intel Core 2 Duo E8500) it took pretty much all night.

Win XP did run some disk checks on next startup, but overall it was a quick & trouble-free experience.  No data lost, so the backups were not needed.  Thanks again.

---

### Post by presence1960 on 2009-12-15
> **Objekt said:**
> Done.  No problems at all.  Resizing the partition went way faster than I expected.  Though it is a very old, slow computer by today's standards (Dell Inspiron 8600 w/Intel Centrino 1.4 GHz single-core CPU), the HDD is only 60 GB.  The last time I resized a partition, it was on a 1 TB HDD and though with a much more powerful CPU (Intel Core 2 Duo E8500) it took pretty much all night.

Win XP did run some disk checks on next startup, but overall it was a quick & trouble-free experience.  **_No data lost, so the backups were not needed._**  Thanks again.

Better safe than sorry. Most times the partioning/install process goes smoothly, but sometimes Murphy's Law reigns it's ugly head, that is why it is recommended to make backups prior to such operations.

Glad you got it working!

---

### Post by Objekt on 2009-12-17
I am happy to report that I freed two people from a Windows-only existence in the past few days.  One had the Dell Inspiron 8600 laptop on which I needed to resize the partitions.  The other user had another ancient Dell machine, a Dimension 2350.  Upon installing Ubuntu 9.10 on the Dimension, we learned its hard drive is on its last legs, with many bad sectors.  That's something Windows probably never would have told us on its own, but Ubuntu made a point of it the first time we got to the Gnome desktop.

Both users were quite pleased with Ubuntu 9.10, and commented that their systems seemed faster than with Win XP.  Hardware that is modest-to-marginal under XP really flies with Ubuntu.  

Certainly, they are not going to be plagued with the malware and virus threats they faced with Windows XP.  One user had installed not one, not two, but THREE anti-spyware/anti-malware programs, all of which conflicted with each other, and had no antivirus software at all.  He didn't need much urging to start doing everything under Ubuntu.  Fortunately, he has no need to use any programs that must be run under Windows.  I used a Wubi install there, because I wasn't sure about resizing partitions, given his dying hard drive.  We will build him a new PC soon, and it will come with only Ubuntu 9.10.

Their printer, an HP Photosmart 1100, just worked straight away under Ubuntu.  I didn't have to do a thing, it simply showed up as an option in Open Office writer, no configuration required.   HP is known to produce Linux-friendly printers, chiefly in that they actually provide Linux drivers for them, but I didn't expect it to be THAT easy!

---

### Post by darkod on 2009-12-17
Well, all three of you, spread the word now!!! :lolflag:

---

