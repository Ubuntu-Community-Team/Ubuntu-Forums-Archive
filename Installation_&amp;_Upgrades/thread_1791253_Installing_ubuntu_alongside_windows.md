---
title: "Installing ubuntu alongside windows"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Christopherjuhl on 2011-06-26
Hi,

I'm trying to install ubuntu 11.04 alongside windows 7 on my brand new HP Pavilion g6. I've burned the installation CD myself, and it seems to be okay. I have some problems, though:

The first time I tried installing ubuntu, I didn't have the option "install alongside Windows", I could only choose to erase everything  or "something else". Then I read somwhere, that I should shrink my windows partition in order to leave some space for ubuntu, so I shrunk it about 20 GB (the harddisk is 500 GB alltogether). Then it actually worked, the option was there "install alongside windows 7". But I wasn't happy with the possible size of the Ubuntu partition, so I went back and shrunk the windows partition as much as I could, to 250 GB. But then, to my suprise, again the option to install alongside had disappeared. It says, I have 250 GB "un-useable" GB. 

So, now I have no idea what to do - I hope someone can help!!

---

### Post by uberl on 2011-06-26
How many partitions are there on your hard-drive created by hp?

---

### Post by Christopherjuhl on 2011-06-26
I think there are four. I have done some extra reading and found out, that four is max - but what do I do, then? 

the partitions are:

(C:)                        NTFS, capacity: 233GB
HP Tools                  NTFS  capacity: 99MB
Recovery (D:)          FAT32  capacity: 17GB
SYSTEM                   NTFS   capacity : 199MB

---

### Post by Quackers on 2011-06-26
Normally people delete the HP TOOLS partition as those tools can be downloaded from the HP site (and you are not very likely to need them anyway).
This will only give you 99MB of free space, so this is not enough to install Ubuntu (or anything else) into :-)
So then you should defragment your C: drive, then in Windows Disk Management screen, shrink the C: drive, by right-clicking the C: partition and selecting "shrink". You then decide how much to shrink it by (in the new window), click on OK and when it's done reboot, twice, to make sure Windows is happy about the change.

After these steps you will get the "install alongside" option in the Ubuntu installer.

---

### Post by Christopherjuhl on 2011-06-26
okay, I already shrunk it, so there is 230GB free. So, if I delete the HP Tools partition, could I then reboot and have the alongside option?

---

### Post by Quackers on 2011-06-26
I believe so :-)

Have you rebooted into Windows to make sure it's happy?
It sometimes doesn't like to have its partitions messed with - especially if it isn't defragmented first!

---

### Post by Christopherjuhl on 2011-06-26
Yes, I have. But I haven't deleted the HP Tools partition yet. Maybe I should create a recovery disk first - I only have a repair disk.
But so far Windows is still happy:)

---

### Post by Quackers on 2011-06-26
Glad to hear that :-)

Definitely create recovery dvd's first!
It's the first thing I do with a new computer.
Actually, I do it twice, with different makes of dvd.

---

### Post by Christopherjuhl on 2011-06-26
Okay, thank you very much! I'll try this tomorrow!

---

### Post by Quackers on 2011-06-26
Ok, good luck :-)

---

### Post by uberl on 2011-06-26
Just encountered same thing with my hp laptop.  Make a recovery disk first.  Then delete the HP_Tools partition and shrink the c drive (already done).  Recommend a tool like easeus to move the recovery partition in front of the newly allocated space to allow it to be merged with the old hp_tools partition.  Now, you should see the option to install alongside windows when you install ubuntu.

---

### Post by nzjethro on 2011-06-26
If it's not too late, I would recomend creating an extended partition in the unallocated space (after deleting HP Tools), and then creating logical drives in that extended partition for /, /home, and /swap (if you want to have them all separate).

The reason for this is that if, down the line, you want to try another distro, or have a blat on a development release, you will find it a lot easier if you have an extended partition (and can therefore just create now logical drives), rather than mucking around having to remove primary drives so you don't exceed your limit of 4.

---

### Post by Christopherjuhl on 2011-06-27
@uberl: I'm not sure what you mean by: "Recommend a tool like easeus to move the recovery partition in front of  the newly allocated space to allow it to be merged with the old hp_tools  partition".  Does that mean, that I don't delete the content of HP_Tools, and how do I merge it with the recovery partition?

@nzjethro: if I choose the "install alongside" option, will it create a swap for me? 

And thank you all very much for the help so far:)

---

### Post by Quackers on 2011-06-27
No, the HP TOOLS partition would still need to be deleted.
The space involved is not worth the risk of moving another partition for, imho.
Yes, the installer should create an extended partition with a partition for root and a swap partition.

---

### Post by uberl on 2011-06-27
Yes, delete the HP_TOOLS partition.  After deleting, you will see partitions in the following order:
-System
-C:\
-Unallocated space (space that you shrunk on the c:\ partition
-recovery
-unallocated space (space from deleting HP_TOOLS)

**The moving partitions is an optional task**
Use of easeus is a personal preference to merge both unallocated partitions.  It can help move the recovery partition so that both unallocated partitions become one.  If done, the partitions will look like:
-system
-c:\
-recovery
-unallocated space

You can get the tool from: [http://www.easeus.com/](http://www.easeus.com/)
Instructions for moving a partition can be found at:
[http://www.partition-tool.com/easeus-partition-manager/help/moving-parition.htm](http://www.partition-tool.com/easeus-partition-manager/help/moving-parition.htm)

---

### Post by Christopherjuhl on 2011-06-28
Now it works perfectly!

I deleted the HP Tools and chose the "install alongside" option

Thanks a lot, everyone!!

---

### Post by Quackers on 2011-06-28
Glad it went well :-)
Happy Ubuntuing!

---

