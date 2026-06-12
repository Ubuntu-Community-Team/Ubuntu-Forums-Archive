---
title: "[SOLVED] Gparted and unallocated space on drive"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Clark Leach on 2008-09-07
So I just installed Ubuntu on my Acer AM1100-B1410A (for the third time today).  Evidently, after telling the installation program to create a 40GB partition for Ubuntu, it ran that through a random number generator and came up with 60+ GB and left me with a chunk of unallocated space on my drive.  I want to reassign this free space back to the Windows partition where I actually stand a chance of using it some day.  Gparted is uncooperative and says it can't even read the ntfs partitions much less change the size.  Is there anything that works???

Disgusted and still disappointed,
C

---

### Post by Partyboi2 on 2008-09-07
Try defraging windows a couple of times and see what happens.

---

### Post by Clark Leach on 2008-09-07
Since the unallocated space is no longer part of a Windows partition how is that going to help?  I initially allocated 40G to a partition for Ubuntu 8.04.1 AMD64 and installed that.  The installation went well, I was just plagued with the same old 64-bit problems (like no Java support); so I decided to install the 32 bit version beside it.  This crashed with a file error about 90% through the process.  Next I deleted all the partitions I had just created and tried to start over again with the DVD that came with the "Official Ubuntu Book".  I told it to create a 40GB partition using free space and ended up with this mess.  I was really hoping Linux had finally become usable; I am so sick of being held hostage by Bill and other "giants".  By usable I mean being able to actually install programs and then use them, like the Sun JDK I just installed but see no sign of.  Ho hum...
I rant and vent

---

### Post by Partyboi2 on 2008-09-07
> Since the unallocated space is no longer part of a Windows partition how is that going to help?
You would be defraging the windows partition in the hope that gparted would then be able to read and resize your windows partition to use the unallocated space.
Can you post a screenshot of gparted?

---

### Post by forger on 2008-09-07
Which release of Ubuntu did you install? Hardy heron 8.04.1?

---

### Post by Clark Leach on 2008-09-07
The current installation is 8.04 from the DVD included in "The Official Ubuntu Book".  I installed all updates online.  I was not given an option at install time to select 32-bit or 64-bit.  I am assuming 32-bit installed since java actually seems to work.  I know of no way to verify this. I will now defrag my Win Doze partitions.

Cheers

---

### Post by forger on 2008-09-07
Did you use that CD to boot from it and use the live cd environment to resize your partitions?
Defragment and scan your ntfs partitions for errors.

The partition editor (gparted) in live cd is at System > Administration > Partition editor

---

### Post by Clark Leach on 2008-09-07
When I rebooted to Vista it scanned the hard-drives and didn't choke.  I then defragged all ntfs partitions in WinDoze.  I tried to specify the partition size during install.  After the install I installed gparted and used it to delete the old partitions which had Hardy 64bit.  I want to reallocate the now unallocated space to the ntfs partition but gparted claims it is unable to read the contents of this file system!  I can access the partitions from Nautilus and open files, etc.  I don't understand.

---

### Post by Clark Leach on 2008-09-07
Using the Gparted live CD throws no warnings or errors and seems to be doing the resizing (slowly).  Go figure.

---

### Post by skunkTrader on 2008-09-07
From the description it appears that you were having problems while attempting to resize the partition while it was mounted.

---

### Post by Clark Leach on 2008-09-08
Yes, I agree.  It seems that the partition was mounted; however, rather than indicate this with the little padlock (like ext3 partitions), Gparted indicates with a yellow warning sign (/!\).  I seem to back in more or less one piece so consider this solved.

Thanks everyone for hints, etc.

---

