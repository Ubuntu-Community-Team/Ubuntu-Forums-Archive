---
title: "partitioning question"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by adamgram on 2008-11-22
I'm trying to set up 2 computers with a dual boot of windows/ubuntu.  I've set up ubuntu a couple of times but have always wiped the drive clean.  This is my first experience with partitioning and I'm running into some problems:

On my Dell Dimension E521, which came with windows xp media center but was replaced with windows xp home edition about a year ago, the hard drive as of now has 3 partitions:  One large one that I work off of, and also two smaller ones.  From what I've read online I think one (41MB FAT16) is the dell recovery portion and the other (5288MB FAT32) contains the drivers that came with the computer.

The partion configuration I'm trying to set up would be 4 partitions, one for windows, one for ubuntu, one for shared files, and one swap.  However, neither the Ubuntu partitioner now G-Parted will allow me to create more than 4 partitions, which means I'd have to delete the smaller partitions to do it that way.

Is this right?  Are you really unable to partition beyond 4 per drive?  I'm not so concerned with the Dell recovery portion, but the drivers I don't want to delete if I don't have to, and also I'm not 100% sure if that's what that is... hmm... so, someone PLEASE HELP!!!

Thanks in advance.

---

### Post by louieb on 2008-11-22
Make the 4th partition an extended partition. Then you can add logical partitions inside of it. (up to 15 on a sata drive) more than that if its and ide drive. 

Unlike windows Linux will install in a logical partition with no problems. 
 [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by adamgram on 2008-11-22
okay!  thanks for the speedy reply... I thought it was something along these lines as I was reading a lot that mentioned extended partitions, but I wasn't quite grasping what they are, what they can be used for, and how to create them...

In the Ubuntu Intallation Manual "Prepare Partions" Screen I have resized my windows partition and created "Free Space".  I click on that and hit 'new partion' and the 'create partition' screen comes up.  Do I create this partition as 'primary'?  I did it this way, and from there I can find no way to create an extended partition inside it.  Also, is Ext3 the same or related to an extended partion?

Thanks a ton for your help.

---

### Post by adamgram on 2008-11-22
oh wait... I think I got it... 'logical' is the same as 'extended'?  well let's just see...

---

### Post by adamgram on 2008-11-22
okay, I got it set up kind of... it made me pick a mount point for my shared partition, and the options were windows or dos.  Neither sounded right, but I chose windows.  Now I can boot in either ubuntu or windows, and in windows I have a second drive (what is supposed to be shared).  In ubuntu, however, I can access the WINDOWS partition just fine, but the partition that I meant to be shared won't show up?!?!  Do I even need to the shared partition?  Is it possible to get windows to see the ubuntu partition just as ubuntu sees the windows partition?  If I change the shared partition to having a mount point of 'dos' will it be visable from both operating systems?

---

### Post by louieb on 2008-11-22
Your shared partiton should show up in the places menu.

A couple of ways to get windows to use the Linux ext3 partitions.
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") 
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")

---

### Post by adamgram on 2008-11-23
Not quite.  The WINDOWS partition shows up in the 'places', but the shared partition is under file system / windows, and cannot be renamed.  I have bookmark for it and can access it from both OS, but it would be nicer to get it in the 'places' with the other partitions, so if anyone has any suggestions, I'm still all ears!

---

### Post by vigya on 2008-11-23
i think d partition where u want to keep all ur files and share, is an ext3 filesystem.
windows cannot read d ext3 file system. so it would not show u dat partition.

ubuntu however, would read ntfs filesystems too.

so u can make that partition ntfs, and use it on both windows and ubuntu.

u can find ur partition at d default disk management of windows.
right click on my computer>manage>disk management(in the left panel)

it will show u all ur patitions with the kind of filesystem they have.
and it will say, unknown filesystem for ur ext3 filesystem..

---

### Post by adamgram on 2008-11-23
No, it Fat32.  Unbuntu see d windows ntfs fine ur right d shared fat32 is seen fine from windows d OS see what they should just d drive not shown in d 'places' and can't be renamed as d file.

---

