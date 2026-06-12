---
title: "Preparing a triple boot."
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by ischwartz on 2014-04-14
Ok so heres my deal, i have two main partitions. Vista and 7. 7 is on the right and takes up all the space and is almost almost full, its a 280gb partition. Then i have a 400gb vista partition behind that that has like 100gb of free space. What i want to do is make the vista partition, that is on the left, shorter so have that unallocated space between the vista and 7 partition, then move 7 back, leaving space all the way on the right for a linux install. 

Is that safe to do? I remember way back when i heard it was unsafe but that was years ago. Im not sure if the situations i read on other threads are the same or not and its kind of a big deal to lose all your data so id like to make sure about my particular situation. Any input is appreciated, thanks.

---

### Post by oldfred on 2014-04-14
Probably, but good backups are really required for any major moves like that.
I might use Windows tools for the NTFS partition changes. 

Have you used all 4 primary partitions? And are both Windows installed in primary partitions?
Windows does have to have the same start & size of the NTFS partition in the PBR or partition boot sector. Usually you have to run chkdsk after any resize or change. And rerun until no errors. Reboot after each change and make sure it still works. Do not try to do too much at once.

Also Windows does like lots of space. You really need 30% free space inside the NTFS Windows partition. At 10% free system will be extremely slow, and defrag just about impossible. 

Windows partition tools
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

But for any Linux activities or new partitions for Linux use gparted on the Ubuntu live installer or download gparted as a liveCD. Windows own partition tool may convert to dynamic partitions if you try to make more than 4 primary. And dynamic is proprietary to Microsoft and does not work with Linux. You can have as many logical partitions as you need, but the extended as a container for the logical counts as one primary.

      
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you have Windows 7 why  even keep Vista?


 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by su:bhatta on 2014-04-15
> **oldfred said:**
> 
Windows partition tools
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)


A year back I had used the EaseUS Partition Master to do the same thing(get my Win8 partition ahead of my data partition) and was successful.
But I also took back-ups for just in case something went wrong.

---

