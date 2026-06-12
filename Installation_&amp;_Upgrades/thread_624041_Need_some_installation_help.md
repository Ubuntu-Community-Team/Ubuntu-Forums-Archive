---
title: "Need some installation help"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by rypicken on 2007-11-26
I just recently downloaded the live cd and burned it to a disc. During installation, I complete the language, the keyboard layout, then it comes to the partitioning. I am currently running on a Windows XP machine looking to be able to dual boot windows/ubuntu. However, the option of resizing my harddrive is not made available. It has a choice to use the entire drive then has a sub bullet with my harddrive listed, use the free space available(which in turn tells me I do not have enough available free space to automatically partition the drive), or use a manual approach. Any suggestions?

Thank you

---

### Post by erfahren on 2007-11-26
try running checkdisk on your Windows two or three times (it's been my experience that all the errors aren't fixed the first time around). You can check the results in the Event Viewer, see: [http://www.housing.hawaii.edu/resources/support/chkdsk.htm](http://www.housing.hawaii.edu/resources/support/chkdsk.htm)

Then defrag it good. JKDefrag works better than the Windows one. It moves everything to the beginning of the partition better. (close as many running processes as you can before running - antivirus, etc.) 

JKDefrag is freeware (of course!): [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

see if that helps

---

### Post by funkyFlash on 2007-11-26
This sounds like your NTFS drive is dirty.  Frankly, NTFS is dirty by nature, but that's besides the point.

If XP is shut down improperly, the dirty bit on your drive never gets reset, so XP will look it over next time it boots.  If Ubuntu comes across a dirty bit being set, it assumes the drive could have problems with it, and doesn't want to mess with it.

Best thing to do is to boot back into XP, (sucks, I know), and properly restart, then put the ubuntu CD in while it's booting.  Hopefully, you'll have more helpful options of resizing the partition and the like.

---

### Post by ZipoTe on 2007-11-26
Try resizing it from Windows using the partition tool you like the most :)

You can also try:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by rypicken on 2007-11-26
is there any free program to partition an ntfs drive? I know partition magic works well, but its at a cost.

---

### Post by rsambuca on 2007-11-26
The best in my opinion is [gparted]("http://gparted-livecd.tuxfamily.org/").

---

### Post by rypicken on 2007-11-27
So i checked for erros and there were none and ran defrag a couple times, and I still lack the option to even shrink my current drive. Any other suggestions?


If I were to partition the drive in windows into a partition for my current OS (XP) and another 15 gig or so partition for ubuntu, how would I go about the installation?

Thank You

---

