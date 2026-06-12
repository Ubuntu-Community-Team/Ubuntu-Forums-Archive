---
title: "installtion error"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by randhir4605 on 2012-04-25
I am installing ubuntu 11.10 amd64  in intel i5 architecture.
During installation in hard disk partion as a primary (dev/sda1) the following error is showing.

The partion /dev/sda1 assigned to starts at an offset of 3584 bytes from the minimum alignment of the disk, which may lead to very poor performance.
                 Since  your formatting this partion, your should correct this problem now by realigning the partion, as .......................................... best suited for the disk.


please help me for this error.


I m selected for the installtion are following

Formate type - ext4
format the partion : yes
mount point : /

---

### Post by techsupport on 2012-04-25
> **randhir4605 said:**
> I am installing ubuntu 11.10 amd64  in intel i5 architecture.
During installation in hard disk partion as a primary (dev/sda1) the following error is showing.

The partion /dev/sda1 assigned to starts at an offset of 3584 bytes from the minimum alignment of the disk, which may lead to very poor performance.
                 Since  your formatting this partion, your should correct this problem now by realigning the partion, as .......................................... best suited for the disk.


please help me for this error.


I m selected for the installtion are following

Formate type - ext4
format the partion : yes
mount point : /

Is this a used computer? Did you reset CMOS before installing Ubuntu? Sounds like the Hard Drive it set at the factory for Windows OS specs.  Maybe if you reset the CMOS?

---

### Post by Mark Phelps on 2012-04-25
Are you trying to reformat an existing partition as part of the install? If so, boot from the Ubuntu CD, select Try Ubuntu, and when you get to the desktop, use Disk Manager or GParted to remove the existing partition.

Then, reboot from the CD and let the installer do the partitioning.

---

