---
title: "First time Linux questions"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by boozker on 2006-12-02
OK I am brand new to Linux, but they looked fun and I wanted to start programming and people said Linux is the way to go. Now i dont want to throw out one of my Windows XP or Mac OS X systems. 

I want to dual boot and i know you have to partition, but i was wondering, before i do this, can i still use all my files that were on me Windows XP or Mac OS X. So i have a partition that is shared by both Ubuntu and Windows XP or Mac OS X and then one to run both Ubuntu and Windows XP or Mac OS X? I know you can, but every tutorial confuses me and is it safe for the files?

Another question is what would be better and/or easier. Dual boot on a Mac OS X or Windows XP? I have both systems. The only thing is my Mac has 80 GB HD and my Windows has 100GB would either be enough?

The MAIN question however is how do i dual boot on one of those systems and don't completely screw up my computer. How safe is it?  When i partition is how do i install on the right drive? I have looked all these things up and never can find answers. They either are to complicated or the people have already partitioned the drive or something.

thanks

---

### Post by cortk on 2006-12-02
Well, there is this guide on how to partition/resize your partitions then install linux to dual boot on windows:

[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html)

But that's all I know of

---

### Post by bulldog on 2006-12-02
Well the screwing up part is entirely in your hands.
Download the gparted live cd and burn it to a disk and boot from it.[25MB]

This is much clearer than the partitioner which comes with ubuntu.
Do your resizing and make the partitions you need for ubuntu,make those partitions after the windows partition,so windows will be the first partition.

A little advice,defragment your windows several times before you do this.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Take your time and look very carefull what you are doing,and all should be fine.

---

### Post by Swankyman on 2006-12-02
Dual Booting onthe Windows XP machine is most likely to the easiest I would say 

Then sharing the files between windows and Ubuntu should be easy enough but remember it is harder to get windows to read a linux formated partition than it is to get linux read a windows partition. i.e 

Ubuntu will read/write to Fat32 and NTFS partitions but its harder to get Windows to read/write to ext3(default linux format) partitions.

If I was you I would re partition your hardrive to three the 1st been Windows, 2nd a fat32 partition for data (both windows and ubuntu can read it, you could use NTFS but the linux drivers for it arent as mature as fat32) and 3rd been ext3 (into which you install ubuntu)

And remember BACKUP all your data before doing anything and then Defrag in Windows to make sure all your data is compacted to the initial part of the partition (so when you partition you dont write over it and make sure there is enough free space to make the other partitions)

After that download desktop installer CD, burn, insert, run, then when you know that ubuntu works (its a live cd so it dont touch the harddrive yet!), 
run installer on desktop of ubuntu, making sure you set up the partitions as above but set the ext3 partition as '/' and bootable and then let its do its thing and wooohooo

:twisted: AND remember BACKUP, BACKUP and then nothing is gone for ever :D 

thats how I did it on mine

Rich

---

### Post by thomashauk on 2006-12-02
Also you may not have to shrink your windows partition at all.

Most oem create a "back up" partition just remove it and install ubuntu on that, easy.

Oh remeber to make a 512MiB partition as swap, this lot seem to have forgotten that point!

---

### Post by Swankyman on 2006-12-02
Well Ive got a corrupted swap partition and thus it never gets mounted at boot time(and cant be bothered to fix it), but because Ive got 1 gig of mem it makes no real difference.

Thus if you got loads of RAM then its not really worth having a swap partition anyway!! unless you are doing really memory intenstive work like code compiling or just having loads of heavy programs running 

But thats my opinion :-k 

:D

---

### Post by digeratess on 2006-12-02
My desktop at work dual boots to Windows and Ubuntu, and until Thursday, my laptop at home did too. (I decided to get rid on windows on my laptop because I haven't booted into it for a couple months.) On my laptop, I have reinstalled Ubuntu quite a few times due to my being pretty new to Linux and messing things up. Plus I wanted to use Edgy, but then decided to go back to Dapper. ANYWAYS, I have done a lot with Windows XP and Ubuntu in the last couple months.

First I want to assure you that the dual booting thing is quite simple. Ubuntu will install GRUB, which is a boot loader that manages booting to multiple operating systems. Other than providing the partitions to install Ubuntu onto, you don't have to do a thing. Your Windows installation will be automatically detected and integrated into the options on the GRUB menu. This will be displayed each time you boot up so you can pick whether to boot to Ubuntu or Windows.

May I suggest, especially since you're familiar with Windows and new to Linux that you use a Windows-based partitioner. I have successfully used the one that comes with Ubuntu, and it's not that bad, but it's kind of a pain and scares me to death every time. When you're performing operations that can completely blow away your OS, I think it's a good idea to use the easiest tool you can find that works.

I do not have enough good things to say about Acronis Disk Director, which you can purchase and download online for $49. This is such a great program. It is so easy to use and has no problems dealing with Linux partitions. What I did the very first time I installed Linux was I resized my Windows partition, which was taking up the whole disk but wasn't full. I did exactly what an earlier poster suggested and created a FAT32 partition to share data between the Windows and Linux OS. I left unpartitioned space for creating a partition for Ubuntu during its install process. It probably would've been easier to just go ahead and set up the Swap and EXT3 partitions in Acronis, but I didn't.

I also use Acronis True Image for Windows to backup partitions. Again, it's extremely easy to use. I back up to external USB drive. You can back up your Linux partitions with True Image from within Windows. How cool is that? This is a separate product, though, and will set you back another $49. If you can't afford to spend $100 on your partitioning and backup, BUY THE BACKUP. I have used this so many times. I don't know how I ever lived without it. If you have a backup you're confident in, you can use the free partitioners and it doesn't matter if you mess it up.

---

