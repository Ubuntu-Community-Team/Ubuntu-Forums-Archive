---
title: "Installer Program?"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by condawg on 2007-05-30
Hi there.
Every time I install Ubuntu, I do something wrong (partitioning), and I end up having to reinstall windows.
I need a program to do the installing and such for me and automatically install a bootloader and partition it correctly so I can have both Ubuntu and my XP.
I tried Wubi with no prevail.
Can anyone kindly assist me?
Thank you !!!!!!

---

### Post by aysiu on 2007-05-30
Well, if the regular installer won't work, and Wubi won't work, I don't know what you can do. Run the live CD, I guess.

---

### Post by merlinus on 2007-05-30
Are you trying to re-size your windows partition to make room for ubuntu?

If so, you may be better off downloading gparted live cd ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) and manually creating the partitions for installation.

And be sure to defrag your windows partition several times, and zero out virtual paging, which can be restored after installing ubuntu.

This page may also help:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

-merlin

---

### Post by acowboydave on 2007-05-30
Hello, I'm a greenhorn to computers, Wubi didn't work? By some slim chance did you have virus software turned off?

---

### Post by jerrylamos on 2007-05-30
An easy way to get Gparted is on Live CD:
System, Administration,  Gparted
if it's not there, then if you have internet access, then Applications, Add/Remove, search Gparted, right click, mark for install, and apply.
Windows always wants to be the first partition on he first disk.  The following assumes Windows is installed and was running O.K.
If Gparted only shows one partition and Windows using all of it, try
boot Windows, Start, All programs, Accessories, System Tools, Disk Cleanup select as much as you can
then Start, All programs, Accessories, System Tools, Disk defragment
usually takes quite(!) a while as Windows attempts to group files together
Look at Details - carefully calculate how much space is left over
You'd need say 4 GB to 10 GB for Linux plus 512 MB swap
If there is that much space, fine.  If not, do
Start, Control Panel, System, Advanced, Performance, Settings, Advanced, Virtual Memory, set both sizes to zero.  You can re-set after Ubuntu install.  Try defrag again and look at Details, is there enough space for Linux yet?
If so, do Live CD Gparted as above, then resize Windows end down no more than the clear space you saw from Defrag Details.  Then you can do a new, 512 MB, file format swap and new, whatever's left, file format ext3.  
Then when you do install, choose Manual partitioning, see if it is still O.K.  If so, Install needs to format the ext3 partition as mount point / and format the swap.
Let us know how you make out.

---

### Post by leadtrombone on 2007-05-31
I would try to adjust the size of your xp partition in xp, in the system tools -> storage. and resize the partition and then install ubuntu to the unallocated space. But I am new to linux so there might be a better way to do it. Someone please tel me if there is a better way.

Brian

---

