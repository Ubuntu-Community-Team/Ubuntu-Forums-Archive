---
title: "ubuntu install not seeing unallocated space"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by gibbogle on 2010-09-04
I burned 10.04.1 to a CD, and have been trying to install it on a Windows 7 machine, following the instructions given here: 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
First I shrank the Windows primary partition, freeing 100 GB of the 500 GB drive.  This shows up in the Windows Disk Management utility as Unallocated.  I expected ubuntu to want to install itself in this 100 GB - this is what the instructions imply.
But when I run the install from the CD, it shows the 400 GB occupied by Windows NTFS, and the 100 GB free, then gives me the option of installing Linux side-by-side with Windows in the 400 GB.  In other words, the 100 GB of unallocated disk space is ignored.  The install program has no flexibility - one cannot choose to use the 100 GB of free space.
Is there something missing from the instructions, or is it that there is something different about Windows 7?  Please help.

---

### Post by gibbogle on 2010-09-04
I gave up the idea of using Windows to shrink the Windows partition and free space for Linux.  I restored the Windows partition to occupy the whole disk, then installed ubuntu from the CD, and let it use 100 GB side-by-side with W7.  The first reboot into W7 invoked a chkdsk, the next reboot started W7 normally.  Selecting ubuntu on the next reboot gave a blank screen with a '_' blinking in the top left corner.  This didn't look good.  I rebooted and this time selected the ubuntu recovery option.  From the menu of options then presented I chose 'update grub' or something similar.  This apparently did something, I know not what.  The next reboot enabled ubuntu to start successfully.  Whew!  Now I have dual-boot W7 and ubuntu. :D

---

### Post by jeight on 2010-09-04
Yeah, I'm sorry that you didn't get a reply fast enough on the first post. When you freed 100gb and you got to the step which said install side-by-side there was another option below that says install to largest continuous free space. That was the option you should have picked. 

You are lucky that it didn't ruin you Windows partition. Wipe the newly installed Ubuntu partition and do the same thing as before but make sure you check the second option during the install. Good luck!

---

### Post by garvinrick4 on 2010-09-04
That is nice it worked out.

If you make a partition before you install Ubuntu you can use manual install and select
the partition and put the / and format ext4 and hit install. / in linux is like C: in Windows and ext4 is what the format is like NTFS in Windows. Here are some gparted how to's that
you might save and read on using gparted a linux partitioning tool that most use I believe.
Will let you see drive in linux form. Read before playing with:
```
Sudo apt-get install gparted
```[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
 [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 
 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 
 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 
 [http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/) 
 [https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions) 
 [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by gibbogle on 2010-09-04
[QUOTE=garvinrick4;9807188]That is nice it worked out.

If you make a partition before you install Ubuntu you can use manual install and select
the partition and put the / and format ext4 and hit install. / in linux is like C: in Windows and ext4 is what the format is like NTFS in Windows.

Actually I did try the manual (advanced) path.  I selected the partition, put '/' and format as ext4.  I was then told that I hadn't selected a swap partition, which was true.  I went back and looked at the selections presented, and didn't see 'swap' among them.  At this stage I decided to abort the install.  What should I have done at this point?

---

### Post by gibbogle on 2010-09-04
> **jeight said:**
> Yeah, I'm sorry that you didn't get a reply fast enough on the first post. When you freed 100gb and you got to the step which said install side-by-side there was another option below that says install to largest continuous free space. That was the option you should have picked. 

You are lucky that it didn't ruin you Windows partition. Wipe the newly installed Ubuntu partition and do the same thing as before but make sure you check the second option during the install. Good luck!

"install to largest continuous free space" I don't recall the third choice being labelled like that.  Anyway, as I've just said in another reply, following that path I didn't see how to provide a swap partition.

At this stage all seems to working fine, so there's no need (AFAIK) to wipe and reinstall Ubuntu.  I must say that I'd prefer to understand the whole process better, though.  Specifically, after space has been freed on the disk, I'd expect the Ubuntu installer to see it as the obvious first choice place to install.

---

### Post by garvinrick4 on 2010-09-04
> **gibbogle said:**
> [QUOTE=garvinrick4;9807188]That is nice it worked out.

If you make a partition before you install Ubuntu you can use manual install and select
the partition and put the / and format ext4 and hit install. / in linux is like C: in Windows and ext4 is what the format is like NTFS in Windows.

Actually I did try the manual (advanced) path.  I selected the partition, put '/' and format as ext4.  I was then told that I hadn't selected a swap partition, which was true.  I went back and looked at the selections presented, and didn't see 'swap' among them.  At this stage I decided to abort the install.  What should I have done at this point?
If you have over 2 gig of RAM you do not really need swap. If you are running on short RAM then swap space is used. When it tells me "you did not make swap space" I just ignore because I have more than 2 gig and do not need. It makes it for if you answer the other way. Still nice just to make a swap partition on your own in gparted from live CD if you need it before install, other wise ignore. You can make all sorts of different partitions / or  /boot or  /home or /data or swap I like them because if I want to do a clean install I do not have to touch my own personal files, everything has its own partition. If you have more than one install you can share the /home so do not have to duplicate. If you make a Extended partition you can put lots of logical partitions inside and it takes only 8 gig or so for an OS, maybe 4 or 5 for the /root and nothing else, share home.

---

