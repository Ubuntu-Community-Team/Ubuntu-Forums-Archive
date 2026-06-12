---
title: "Dual Boot Problems"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by thepoplin on 2007-02-14
So basically I'm kind of newb to Linux and my buddy told me to try Ubuntu out on my free XP space. So I repartitioned the drive and gave about 500 to swap and 10 GB to Ubuntu. So now Ubuntu runs flawlessly and lets me even browse my other Windows partition and play my music, retrieve papers, etc. etc...
One problem. I tried to boot XP yesterday and the good old BSOD popped up with "Unmountable Boot Volume". I've searched all over the forums with no simple answer. I tried the FIXMBR and CHKDSK /R in Recovery Console with no avail as well. But here is my FDISK data:

poplin@poplin-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       50790    25598128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           50793       76198    12803805   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           76198       77520      666697+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
poplin@poplin-laptop:~$ 
poplin@poplin-laptop:~$ 


Not ending on cylinder boundary...that doesn't sound good - but what do I know. My instinct tells me that Windows is getting pissy at not being the primary partition but I'm not sure. Even if I was I wouldn't know where to start. Unless someone figured out how to get Visual Studio 2003 to run on Ubuntu, I HAVE to have XP running or it's nuts and bolts for me. Thanks.

---

### Post by mssever on 2007-02-14
> **thepoplin said:**
> So basically I'm kind of newb to Linux and my buddy told me to try Ubuntu out on my free XP space. So I repartitioned the drive and gave about 500 to swap and 10 GB to Ubuntu. So now Ubuntu runs flawlessly and lets me even browse my other Windows partition and play my music, retrieve papers, etc. etc...
One problem. I tried to boot XP yesterday and the good old BSOD popped up with "Unmountable Boot Volume". I've searched all over the forums with no simple answer. I tried the FIXMBR and CHKDSK /R in Recovery Console with no avail as well. But here is my FDISK data:

poplin@poplin-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       50790    25598128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           50793       76198    12803805   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           76198       77520      666697+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
poplin@poplin-laptop:~$ 
poplin@poplin-laptop:~$ 


Not ending on cylinder boundary...that doesn't sound good - but what do I know. My instinct tells me that Windows is getting pissy at not being the primary partition but I'm not sure. Even if I was I wouldn't know where to start. Unless someone figured out how to get Visual Studio 2003 to run on Ubuntu, I HAVE to have XP running or it's nuts and bolts for me. Thanks.

You're right. Not ending on a cylinder boundary doesn't sound good, but I don't really know for sure. My XP partition has the boot flag set (it's the only one that does). You should check that. Otherwise, maybe you could install XP in VMWare ;)

---

