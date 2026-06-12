---
title: "Is 30Gb the largest option during dual-boot install?"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by ShermW0829 on 2013-06-15
I am installing on a Vista laptop with over 170Gb available. When I run the Ubuntu install it seems that I can not select more than 30Gb. Is there a way to have over 30Gb for Ubuntu?

Also an off-topic question. Since WinXP is not supported anymore can we now have more than one computer running the same WinXP?

Thanks in advance;

Sherman

---

### Post by JRV on 2013-06-15
Are you trying to do a WUBI install?

If you are doing a full install you can change the size of the Linux partition. 
With WUBI it's not so easy, ask the question in the WUBI subforum.

Microsoft has not turned off the product activation for XP yet, and I doubt they ever will.

---

### Post by Frogs Hair on 2013-06-15
Wubi has a 30 GB limit and is for trial use with Win 7 or earlier . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ShermW0829 on 2013-06-15
Thanks to all.

---

### Post by kurt18947 on 2013-06-15
> **JRV said:**
> Are you trying to do a WUBI install?

If you are doing a full install you can change the size of the Linux partition. 
With WUBI it's not so easy, ask the question in the WUBI subforum.

Microsoft has not turned off the product activation for XP yet, and I doubt they ever will.

I read some time ago - can't say where - that one of the last XP updates would be to remove the activation mechanism and turn off the server(s).  Frankly, once MS support ends what would be the benefit to maintaining product activation.  It's not like there are no hacked/cracked copies of XP  around.  How wise it would be to run XP except in a very restricted environment with no outside access would be another discussion.  If I were a blackhat and discovered an undocumented exploit knowing  XP updates would end in a few months, why not sit on it until May, 2014?  Then there should be no fix from Microsoft and the exploit should remain available for my pleasure and profit unless a 3rd party steps in.  You *know* XP is going to continue to be used online after April 2014.

---

### Post by Mark Phelps on 2013-06-15
If you're going to dual-boot, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Vista Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

Use only the Vista Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Vista, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.

Once you have Vista shrunk, when you then boot back into the Ubuntu installer, use "something else" to do the partitioning.

---

