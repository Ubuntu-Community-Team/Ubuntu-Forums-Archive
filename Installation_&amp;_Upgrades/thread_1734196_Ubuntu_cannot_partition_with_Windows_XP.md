---
title: "Ubuntu cannot partition with Windows XP?"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by ondamnedwings on 2011-04-20
Hi guys, 

I'm completely new to Linux, but I'd really love to try it. 
My issue is that I CANNOT get my HP Compaq 6510b to repartition. 
I've used to GpartEd to try and shrink c: (off of a GpartEd Livecd) but it doesn't give me an option other than an adding an extra 3mb. Also, when I try to install Ubuntu it only gives me two options: erase everything and install Ubuntu (10.10) or manual, not the dual boot option (which is really what I'm looking for). 
I've defragmented it about 6 times by now and I don't think it's going to get much better. 
I'm kinda new to this kind of stuff, so if you need more info let me know. 
It'd be really great to try out Linux (aside from off the CD...).
:confused:

---

### Post by tommcd on 2011-04-20
You should use manual partitioning for best results. Choose to shrink the XP partition to leave enough unallocated space for Ubuntu. 
How big is the hard drive? And how much space do you want for XP.
Create 3 partitions for Ubuntu: root (where the OS lives), swap (this is analogous to virtual memory in XP), and home (where your user specific settings and data are stored).
Here is a good tutorial to get you started:
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
That tutorial uses Windows7; but it is essentially the same for XP. It is even easier with XP, since XP does not use a separate boot partition like Windows7 does.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Mark Phelps on 2011-04-20
Did the Compaq come preloaded with Vista (or win7)? If the answer to either is yes, do NOT use GParted to shrink the OS partition -- unless you don't want to use Vista/Win7 anymore.

Windows won't let you shrink a partition very much some times for good reasons -- doing so will corrupt the filesystem, rendering Windows unbootable.

Use the Windows Disk Management tool to do the OS partition resizing, not GParted.  See the link below for some hints on stuff you can to do try and get more shrinkage:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by tommcd on 2011-04-21
Herman's tutorial that I linked to in my last post uses the Ubuntu partition tool to shrink a Windows7 system partition:
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
> There's no evidence to suggest that Windows own partitioning software is really any more reliable than any other partition editor but if you damage your Windows system with its own software it's no concern for me or other proponents of open source.
I have read about this problem with Windows7 before though. Perhaps it depends on how much you shrink the Windows7 system partition.
You can get Windows7 recovery discs here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Quackers on 2011-04-21
How many primary partitions already exist on your system?

---

### Post by oldfred on 2011-04-21
I still also recommend using windows MMC to shrink windows Vista/7. But have read several posts from Herman explaining the issue. Gparted and the install supposed always worked. But older versions of gparted that started partitions at sector 63 (when windows was normally at sector 2048 ) would move the start of the windows partition to sector 63 unless a check box was cleared.

Herman on checkbox resize partitions - post #7
[http://ubuntuforums.org/showthread.php?t=1629113](http://ubuntuforums.org/showthread.php?t=1629113)

Windows will always want to do chkdsk after any resize, but windows also requires internal data on partition size in the partition boot sector to match the actual partition and partition table. A combination of chkdsk and fixboot would usually fix the issue if the partition was moved.

But new versions of gparted now also start partitions at 2048, so that issue is gone. But we do not know if a user has an older gparted and does not know about checkbox, so it still is a bit safer to suggest using windows to resize windows.

There also have been issues with some windows tools, not sure if windows or third party windows partitioning tools. Some do not see the Linux partitions and rewrite partition table incorrectly. So only use win7 MMC to shrink windows before any Linux partitions are created.

---

