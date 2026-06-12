---
title: "choosing the partition"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by AndyH-uf on 2011-07-14
Your registration process has no sense of humor.

I would like to install Ubuntu to create a dual boot computer along with my Windows 7 system. The answers I need may already be somewhere in the hundreds, or thousands, of posts I did not read, but my efforts so far have mainly brought up approaches that don't interest me and tales of other's  peoples failures.

Perhaps someone can point me in the proper direction where the successful install is describe in sufficient detail for me to be able to see what I need to do. Perhaps I could just proceed to install and would find that the process allows me to do what I want, but I have not been able to obtain a clear idea of that. I want to just stay away from something that is going to make the entire computer unuseable for days.

I do not want to modify the Windows OS partition in any way.

I have two hard drives. Each has three primary partitions (100GB each) and one extended partition (500GB - 3X100GB). All are NTFS. The first partition of drive 1 is Windows, the other partitions are my way of arranging my projects and my data to best suit my interests and convenience.

I want to put the Linux system on the third partition of drive 2. Besides moving anything currently there to somewhere else, I don't  understand if I have to do something to the partition itself before I start to install. 

If I understand Linux requirements, I need at least one other partition. I want to carve that out of the extended partition (partition #4) of drive 1. Should I do that before starting the install? I am willing that this test Ubuntu system have 200GB total to itself, but am more inclined to take only 50GB from partition 4 of drive 1 instead of 100GB, giving 150GB total.

If necessary, I can move my data around and clear partition 1 of drive 2 for Linux, instead of using partition 3, but this is not my preference.

Will it work to put Linux on the second drive instead of sharing the first  drive with Windows?

Will it work to use partition 3 of drive 2?

Does my intended plan seem to embody any fatal misunderstandings?

I have played with Ubuntu a little from a USB flash drive. Can I accomplish what I described above by creating an install CD-R from the same download I used to make the flash drive system (ubuntu-11.04-desktop-i386.iso), or do I need to start with something else?

---

### Post by dino99 on 2011-07-14
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Mark Phelps on 2011-07-14
Some important caveats ...

First, regarding partitioning, you can not install Ubuntu to an NTFS partition.  So, you will have to remove one to make room.  Don't partition the new unallocated space -- let the Ubuntu installer do that.

If you have an optical drive on your PC, BEFORE you do the dual-boot setup, boot into Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot loader.

Don't allow the installer to shrink any Win7 OS partitions, instead, if you have to shrink such a partition, use the Win7 Disk Management utility to do so.  Then, reboot into Win7 a couple of times to allow it to make any filesystem adjustments.

---

### Post by AndyH-uf on 2011-07-14
After a couple more hours reading, I deduce that the best course for my current interest is.

Within Windows
shrink the 4th partition of drive 2 (a logical partition completely occupying an extended partition) to make about 100GB of unallocated space.

do the same with the 4th partition of drive 1, producing about 50GB of unallocated space.

Write an Live CD from ubuntu-11.04-desktop-i386.iso

Write a Win 7 repair CD

shut down Windows



Boot from the Live CD

created a root partition and a home partitions in the unallocated space of drive 2

created a swap partition in the unallocated space of drive 1, holding the remainder of that 50GB in reserve for future use

install Ubuntu

Any comments on obvious errors appreciated.

---

### Post by oldfred on 2011-07-14
Swap does not have to be huge, current rule is 2GB or the size of RAM if you want to hibernate. If you have 4GB or more of RAM you may never use swap, but should have some.

I like to keep all system files on one drive. Keep all of windows on sda, and all of Ubuntu on sdb. You can mount all your NTFS data files from either drive. But if the windows drive fails you can boot Ubuntu and vice versa. 

I also prefer smaller system partitions and larger data partitions. You already have lots of data partitions, so you do not need a large /home or can leave it inside / (root). You still need to back up /home as it has user settings, but if all your data is in the other NTFS partitions it will not be large.

Herman has lots of detail. Not as complex as it may first seem as he try to explain everything.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by AndyH-uf on 2011-07-15
Things seem to have worked out well. Following what I outlined above, I was able to install in  straightforward way. Creating the Linux partitions was a little perplexing. The information I had to choose or enter was different from the detailed step by step instructions I read in the community documentation but I apparently made the right choices because it all seemed to work. The system installed and I was able to play with it for an hour or so, until I wanted to install the modem and get online.

However, thereafter I ran into problems, as described
[http://ubuntuforums.org/showthread.php?p=11049471#post11049471](http://ubuntuforums.org/showthread.php?p=11049471#post11049471)

I must have done something to cause this. I did change a few customization settings, but nothing I can in any way identify with the problem. I haven't figured out anything that fixes it.

---

