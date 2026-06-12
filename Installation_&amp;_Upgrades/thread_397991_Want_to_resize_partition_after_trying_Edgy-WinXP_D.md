---
title: "Want to resize partition after trying Edgy-WinXP Dual Booting"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by clarose on 2007-03-31
I have been using Ubuntu Edgy for quite some time now and also on this system I can dual boot to WinXP Home.  By the way, VMWare server is a awesome product - installed XP under Ubuntu and it all works flawlessly - even VPN.

Anyway, after installaing Nvidia, Beryl, etc and all the bells and whistles, I wish I could resize the partitions again in a more serious way.  I don't want to start all over.  My dream would be to boot to XP, move files around - shrink its usage then back to Ubuntu and resize the partitions up more for linux.

I've been playing with Ubuntu for so long now, it's now not playing but actually working on it professionally so...guess you could say that I wanted to try it out but that was so wildly successful that I want to make this home now but still leave a little pure XP available.

What's the best way (if any) to partition things around a bit?  Want to shrink WinXP down and expand Ubuntu.  Need to save real XP for gaming and Cubase work - prolly only about 20GB.

Have two drives - 160GB and 320GB.  160 is where Ubuntu resides with WinXP.

Sorry to be so long winded but I want to be perfectly clear.

Thanks

---

### Post by matt91 on 2007-03-31
the live cd had a partitioner built in or it can be installed through synaptic on the live cd by searching for gparted. thats how i resized mine.

to be sure it wall resize well make sure the windows is defragged.

---

### Post by melenor on 2007-03-31
i have ubuntu and windows on my PC and i need a slightly more room for windows and i have already cleared and formated the parition (D:\ drive) i want to merge with the C:\ Drive  and i was wondering if i did your way would i still be able to boot without having to do any editing in windows or ubuntu?

---

### Post by zvacet on 2007-04-01
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by clarose on 2007-04-02
Well, the issue is one that I need some conceptual help on.

Using gparted, I shrunk the Windows NTFS partition down a few GB and then I had an open partition "in front of" my linux ext3 partition. 

So I was able to shrink the NTFS partition but don't know if it is possible to now "upsize" the existing ext3 partition.  It seems like it is at its maximum.  All I can do is to create another partition between the NTFS and ext3 partitions.

Is it possible to add the new (and as yet undefined) partition to the existing ext partition?

Thanks

---

### Post by todoporron on 2007-04-02
Hi.

Give a try to the gparted live CD, I resized mi partitions with this utility which works very well.

---

### Post by clarose on 2007-04-02
Will the gparted live CD allow me to combine the new partition (after shrinking the NTFS partition) with the existing ext3 partition?

I don't want to download, burn and boot another CD if I'm going to have the same situation.

1) I shrink NTFS partitition
2) I am left with an undefined partition and pre-existing  ext3, swap, etc
3) I cannot seem to understand how to increase the existing ext3 partition so that it can use the new undefined partition.  It already says it is at its maximum.

Thnx

---

### Post by serfcx on 2007-04-02
(Using the GParted Live CD)
After resizing your win NTFS you should now have an area called "unallocated space".
Use GParted to move your / partition, and followed by your swap into this space - click on the partition in the space diagram and use the resize/move button and drag the partition to the left for both / and swap. Then you can move on to enlarging your /home partition to take up the available space by using the resize button again.

**back up your data first**

---

