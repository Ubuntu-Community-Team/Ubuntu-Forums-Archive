---
title: "Shrinking/extending"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by S. Vaden Blue on 2010-09-19
I have 60 plus GBs of free space left in my Vista partition that I would like to devote to my ubuntu install. Can someone please help me? I'm admittedly a noob so ANY help would be greatly appreciated.

Thanks,
S. Vaden Blue

---

### Post by Rubi1200 on 2010-09-19
I am not sure about Vista, but you want to look first if you can use the built-in disk management tools to shrink the drive.

Barring that, probably the safest method is to boot an Ubuntu CD in live mode and use GParted (which is on the CD) to do the work.

Make sure you backup any data first!!

And, before installing Ubuntu, boot back into Vista to make sure everything is okay.

---

### Post by Lateralis on 2010-09-19
You absolutely definitely should shrink the Vista partition using the inbuilt Vista disk managment tools.  I did this when I made space for Ubuntu on my then new laptop.  Making changes to nfts partitions using gparted or any other Linux disk management program is fraught with danger.  

Of course, always make sure that your data is fully backed up on an external medium - DVD/CD, external hard drive or USB flash drive -  before making any changes to the computer.  I know this goes without saying, but I feel better for saying it! 

In order to grow the Ubuntu partition it must be unmounted.  Because of that you cannot do this action whilst in Ubuntu.  You must boot from a LiveCD and use gparted.  

The one potential pitfall is if Ubuntu is installed in an Extended partition and (almos certainly) Vista isn't.  You may find you have to first grow the extended partition before you can grow the Ubuntu partition within the Extended.  Or, you might find you can't grow the Extended partition.  I don't know as I've never done that before, but I'm sure someone who has done that before will clarify. :)

---

### Post by S. Vaden Blue on 2010-09-19
I already have Ubuntu installed. I just want to add the free space in Vista to the current install.

---

### Post by Rubi1200 on 2010-09-19
Aha, there was a misunderstanding there oops :)

Can you please post a screenshot of the current setup from either Windows or Ubuntu?

---

### Post by S. Vaden Blue on 2010-09-19
I still have to unallocate the space from the Vista partition. Should I show you the screenshot before or after? Maybe it would help if you see what I have thusfar?

---

### Post by S. Vaden Blue on 2010-09-19
Included is the screenshot of disk allocations. Other is Ubuntu and SW-preload is Vista. These are from EASEUS Partition Manager (Windows.
[ATTACH]169969[/ATTACH]

---

### Post by Rubi1200 on 2010-09-19
Ok, so you want to shrink the Vista partition and then grow the Ubuntu partition to the left including the space currently marked as unallocated correct?

---

### Post by S. Vaden Blue on 2010-09-19
Precisely. Actually, the unallocated space to the left is from using the Windows Disk Management utility for shrinking.

---

### Post by Rubi1200 on 2010-09-19
Ok, so shrink the Vista partition to where you want it and then post another screenshot and we will take it from there.

Thanks.

---

