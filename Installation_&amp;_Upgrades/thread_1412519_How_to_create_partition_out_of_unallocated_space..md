---
title: "How to create partition out of unallocated space."
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by ankurk on 2010-02-21
Hi Guys i have 160Gb single hard drive.

please refer to screen shot below
[IMG]http://img31.imageshack.us/img31/5461/snapshotj.jpg[/IMG]

Now c: is vista

The partition of 30gb contains red hat linux 

so i am having dual boot on my dell laptop M1530

Now i would like to use the unallocated 80 gb space in vista.
 I am not able to create a partition out of it. it says not enough space fot the operation.

Please help.

The reason i am posting here is i wanted to make my machine tripple boot with ubunto , but the live cd doesnot detect windows os. so i thought to use the unallocated space in windows and use vmware in windows to install ubuntu,

Khurana

---

### Post by darkod on 2010-02-21
Strange. You should be able to just right-click on the 86GB unallocated space in this window in Disk Management and select something like Create Primary partition. You only have 3 partitions and the limit is 4 so there is no reason not to allow you that.

---

### Post by C.S.Cameron on 2010-02-21
I understand that you are only allowed four partitions per disk.

---

### Post by ankurk on 2010-02-21
> **darkod said:**
> Strange. You should be able to just right-click on the 86GB unallocated space in this window in Disk Management and select something like Create Primary partition. You only have 3 partitions and the limit is 4 so there is no reason not to allow you that.

Thanks for the reply. exactly i tried as you said but still error. any way out like some third party softwares??

Thanks.

---

### Post by darkod on 2010-02-21
You could try Gparted from ubuntu live desktop. It can create ntfs partitions.

---

### Post by ankurk on 2010-02-21
> **darkod said:**
> You could try Gparted from ubuntu live desktop. It can create ntfs partitions.

Sir i tried with acronis disk directory free version.  But i cannot commit the operation. is there anyother software that can do it for free. partition magic is not working either.

problem with Gparted is it will not even detect the partition it shows the whole hard drive as empty.

:confused:

Ankurk

---

### Post by darkod on 2010-02-21
> **ankurk said:**
> Sir i tried with acronis disk directory free version.  But i cannot commit the operation. is there anyother software that can do it for free. partition magic is not working either.

problem with Gparted is it will not even detect the partition it shows the whole hard drive as empty.

:confused:

Ankurk

That might mean the hdd has some faults or maybe a bad sector. Gparted is usually very good working with hdds. Maybe that's why creating the partition from windows is failing too.
Have you tried running chkdsk from windows? Try to google for instructions how to use chkdsk, I haven't used that command and don't know the exact syntax.

Or even try to find a tool from the hdd manufacturer and run it to check the disk for errors.

---

### Post by tad1073 on 2010-02-21
unmount the mediadirect partition and create an extended partition on the 86gb then format to what suits you.

---

### Post by ankurk on 2010-02-21
> **tad1073 said:**
> unmount the mediadirect partition and create an extended partition on the 86gb then format to what suits you.

Ok done i used EASEUS Partition Master 5.0.1 Home Edition

Did the trick for me...

Thanks for your valuble time :)
Cheers 
Ankurk

---

