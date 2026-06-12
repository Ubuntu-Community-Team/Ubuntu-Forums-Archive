---
title: "Kernel 2.6 Parted bugs 1532 drive geometry break on install?"
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by Bagleemo on 2004-10-20
Greetings -

This is just to find out if the bug in Parted that was with the pre-RC version of warty ever got fixed. I've been on bugzilla but can't quite determine if the fix was incorporated in the final release or not.  This was listed as bugs 1566 and 1532.  The bug was that after install, the drive geometry would get corrupted such that Ubuntu would work, but Windows installs on the same drive would not boot and give the NT Chainloader error.  

This bug whacked my Windows install last time I tried to install Ubuntu... I was mighty sad as spending all that time rebuilding my Windows partition was a drag.  So I don't want to try again until I know that bug is fixed....

-Amos

---

### Post by Bagleemo on 2004-10-21
Oh man... that is so lame that this wasn't fixed prior to releasing. 
It sure seems like many, many people are going to get turned off from linux as a result of this parted bug.  

If someone has browsed to this message because they have had the same problem:  i.e. if after installing Ubuntu (or many other linuxes using kernel 2.6 as well) you cannot boot Windows and instead halt with an NT Chainloader message -  

Enter your system bios and set the hard drive in question's access mode to LBA (not Auto or CHS).  This should allow your system to boot Windows and Linux.  More info on this bug can be found here:
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/)

---

### Post by oldi on 2004-10-21
I did have the same problem when i installed FC2 and i really made a mess with my computer. I was about to install ubuntu, after hearing so many good comments about it, hopping that they would have solved this problem. But now am not sure whether to install it or not.

Is it possible not to install GRUB on a partition but to install it on a floppy so that every time i want to use ubuntu i boot from the floppy? Would this solve the problem with the table of partition? 

I would love to install ubuntu, so any help on this will be appriciated
thanks

---

### Post by Bagleemo on 2004-10-21
Ok - I really don't know this for sure so please take with a grain of salt.
As I understand it, this bug is caused by parted, which does something windows thinks is bad to the CHS values on the partition table. The link in my previous post talks about how to fix it.  On my system just telling the bios that my drive is LBA mostly fixed it and my windows will boot, except now windows thinks my FAT32 partition is unformatted (which sucks the big one, cause it has lots of stuff on it.)

I don't think this problem has to do with the MBR, or with grub.

This is a complete guess - but I imagine that if your system already has the necessary partitions setup to install a linux on, and you don't adjust the partition scheme at all during ubuntu's install, then this problem shouldn't happen.  Again, this is a total guess based on my belief that the partitioning tool the ubuntu installer uses (parted) is the source of the problem, and that if you don't ask the installer to partition anything it won't use parted and therefore won't hose things up.

The main thing to remember is to follow the instructions described in the link in the post above if you install ubuntu and your windows won't boot.  DO NOT use any partitioning tools to fix it, or run fixboot or fixmbr or anything.  As long as you follow the instructions this is supposed to be totally recoverable.  

I'll update more later when I (hopefully) fix my fat partition.

-A

---

### Post by Bagleemo on 2004-10-21
Following instructions from link above worked ok- my drive now knows it has 256 heads again which is nice.  However, my fat32 partition containing my music files is still seen by Windows as unformatted as a result of the ubuntu installation.  Anyone got any tips? 

Thanks -

Amos

---

### Post by AlainBougrain on 2004-10-22
Hi everybody,

The same problem exists under Suse 9.1, FC2, Mandrake Com 10.1 &amp; surely many others based on 2.6 kernels.

I hope cross-distrib posting is permitted and I invite you to read [http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html) as the problem is clearly explained.

One tool to solve this problem is [http://www.cgsecurity.org/index.html?testdisk.html](http://www.cgsecurity.org/index.html?testdisk.html).

Regards,

---

### Post by Bagleemo on 2004-10-23
Alain - 

Thanks for the reply and for the recommendation.  One way in which the problem I saw differed from the explanation is that fixing the partition table according to the instructions I had seen (by setting the number of heads back to 255) did not completely solve the problem.  It did allow my windows and linux installs to boot, but my swap partition and my fat32 partition (designed to be accessed by Windows and Linux) were never recovered. I had to reformat them.  All seems well now though.

I hadn't seen anything about this sort of eventuality occuring in the bug reports / etc. that I've read.  So I'm wondering if I should add the details of my experience to the mix. What would be the best way to do this - another bug on bugzilla? Or what? 

Again, thanks very much for your assistance -

Amos

---

