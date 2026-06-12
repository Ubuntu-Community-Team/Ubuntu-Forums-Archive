---
title: "Failed install, missing partitions"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by stillmitch on 2010-01-03
I was trying to install Ubuntu as a dual-boot on my Windows Vista laptop. The hard drive is 250 gb: Vista boot 157 gb partition; a partially-occupied 33 gb partition which was designated as swap-space; a newly partitioned and ext3 formatted 30gb for the Ubuntu installation.

I believe there is also a hidden partition ~20 gb with "hidden" system info. 
During installation I received an error message concerning the swap space partition, which forced me out of the installation and back to the ubuntu partition manager screen. Now in Vista my 33 and 30 gb partitions are missing. 

I'll admit I'm a complete novice and jumped into this without doing enough research. Is there anyway I can get back to pre-Ubuntu state? Any help would be very greatly appreciated. 

Thanks

---

### Post by tripolitan on 2010-01-03
To undo, you pretty much have to know the original state of your 250GB HD, if you don't, I don't see how anyone could help. 

If you have installed Vista on your own, there should be one partition, unless you made a second one for swap. I don't understand how and why you have a hidden partition (unless it was prepared for system restore or recovery) but in any case, you'll have to boot into Ubuntu using the CD and run gparted, delete all partitions EXCEPT Vista's NTFS partition. After that you expand your Vista partition to occupy the rest of the HD (you'll hopefully end up with approximately 250 GB in one partition, and just continue using Vista.

---

### Post by stillmitch on 2010-01-03
Got it straight. Thanks!

---

### Post by Sef on 2010-01-03
> The hard drive is 250 gb: Vista boot 157 gb partition; a partially-occupied 33 gb partition which was designated as swap-space; a newly partitioned and ext3 formatted 30gb for the Ubuntu installation.

Swap should not be more than 1 GB.   If you need more, then you should get more ram.

If you partition with Vista on your system, you will be unable to boot into Vista afterwards.   Read [Gparted's FAQ #9]("http://gparted.sourceforge.net/faq.php") for what to do.

---

### Post by tripolitan on 2010-01-04
Sef, thanks for the tip re. Vista/Gparted

---

