---
title: "Dual boot with Windows 7, SSD"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by CorruptDNA on 2014-07-15
Hi guys!

I just need some help and general push in the right direction. You see i have installed ubuntu countless times before but today i would like to do it on a ssd. Now the thing is, i want a lot of things to stay the same way and want to know what to do without screwing up anything.
So what i want to do is keep my current windows 7 installation and install ubuntu 14.04. Now that's not so hard, but the problem is i want to install it on my ssd. At the moment, i have a ssd and a normal hdd installed on my laptop. I have installed windows 7 on the ssd and have currently around 50 GB of free space left. 300 gb on the hdd. What id like to do is install ubuntu on the ssd without screwing anything up and still keep around 10-15 gb left in the ssd. My question is, if i am successful in installing ubuntu on my ssd by partitioning it somehow, can i install my future programs on the hdd? 
My other question is, will my ssd slow down or anything? Will it be useful to install ubuntu on it or should i just install it on the hdd? (if so, then i can do that without screwing up anything) 
Also i heard that there is trim support and stuff .. (i dunno anything about that.. so .. well .. my ssd is transcend? )

Well if you need to post anything, do tell. 
Also first step, download ubuntu 14.04 (check), make bootable usb( check) ,  partition enough space for ubuntu etc (need to do)..

ill attach a screenshot of my current disk management to give you guys an idea. what should i do next?

---

### Post by mastablasta on 2014-07-16
no problem there. defragment and then shrink your Windows partition. run checkdisk.  make space for ubuntu and install ubuntu into the empty unformated disk space (select to install into largest free space).
> 
 My question is, if i am successful in installing ubuntu on my ssd by partitioning it somehow, can i install my future programs on the hdd? 
yes, but you actually would want to have programs on SSD so they start, load and run faster.

 > My other question is, will my ssd slow down or anything?
no, quite the opposite should happen ;)

 > Will it be useful to install ubuntu on it or should i just install it on the hdd?
for sure. just like it is useful for windows to be on SSD. you will get ludicrous speed :)
)

>  (if so, then i can do that without screwing up anything)

yes. see my first comment.

---

### Post by CorruptDNA on 2014-07-16
ok then, so to install ubuntu on the ssd, i make a seperate partition from the ssd (15 gb enough?)  and also make another partition from my normal hdd (12gb ) for swap. and then when installing ubuntu, mark the first one (the ssd partition) as ? and the hdd one as swap to install ubuntu?

---

### Post by yancek on 2014-07-16
15GB should be enough for the root filesystem partition.  12GB seems like an excessive amount for swap, 2GB should be more than enough.  How much RAM do you have?  

>  mark the first one (the ssd partition) as ? 

Not sure what you are asking here, the filesystem type?  The default would be ext4 on which to install Ubuntu.

---

### Post by CorruptDNA on 2014-07-17
> **yancek said:**
> 15GB should be enough for the root filesystem partition.  12GB seems like an excessive amount for swap, 2GB should be more than enough.  How much RAM do you have?  



Not sure what you are asking here, the filesystem type?  The default would be ext4 on which to install Ubuntu.

i have 8 gb ram.. dunno how much i should keep as swap..

---

### Post by yancek on 2014-07-17
2-4GB should be more than enough.  Depending upon what you use the computer for, you may never need it but, better to have it and not need than need it and no have it.

---

### Post by oldfred on 2014-07-17
Your first post shows sdb as dynamic. That is a huge problem.

Linux only works with basic partitions. 

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by mastablasta on 2014-07-18
E is dynamic but the OP is not installing to E partition but on different disk as i understood.

@[**[COLOR=#000000]CorruptDNA[/COLOR]**]("http://ubuntuforums.org/member.php?u=967240") you will still do good if you follow oldfreds advice and convert those to basic.

about swap - /swap is like pagefile.sys in Windows. so if you plan on hibernating it should be the same to the amount of ram you are using. however if oyu don't plan to hibernate or if you plan to hibernate after shuting down all programs then 4GB is more than enough. you might even get away with no /swap. basically this part of disk get's used when you run out of ram. so ram of inactive apps is dumped there. 

this is the reason that ocmputer wiht low ram are slow, since moders OS and applicaitons need quite a bit of ram and when they run out they use the hard disk. which is A LOT slower than RAM in read&write speeds.

---

