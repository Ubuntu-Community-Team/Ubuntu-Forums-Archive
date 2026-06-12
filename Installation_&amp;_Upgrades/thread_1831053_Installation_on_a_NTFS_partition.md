---
title: "Installation on a NTFS partition"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by deadset22 on 2011-08-22
Hello everybody.

I new to Ubuntu and wanted some advice. I planing to build a new computer and wanted to use a SSD to dual boot win7 and ubuntu 10.10. What I wanted to know is if Ubuntu 10.10 will install on an NTFS partition or if when I partition the SSD will I be able to set one partition to one file system and the other partition to another file system, this way I wont need to get two SSD's.

Thank for any help you guys provide.

---

### Post by dave01945 on 2011-08-22
just partition the drive one NTFS for windows and one ext4 for ubuntu you can use different filesystems on different partitions on the same drive

---

### Post by b2zeldafreak on 2011-08-22
> **deadset22 said:**
> Hello everybody.

I new to Ubuntu and wanted some advice. I planing to build a new computer and wanted to use a SSD to dual boot win7 and ubuntu 10.10. What I wanted to know is if Ubuntu 10.10 will install on an NTFS partition or if when I partition the SSD will I be able to set one partition to one file system and the other partition to another file system, this way I wont need to get two SSD's.

Thank for any help you guys provide.

To answer your question: You can have up to 4 primary partitions and a lot more extended partitions. Each partition can be a different file format if you like. So in your case you will be able to install Windows to NTFS, and Ubuntu to ext4. 

(Just for reference Ubuntu can be installed to an extended partition, but you will probably just want to install it to a primary.)

So in your case, I believe you will want to install Windows first and then Ubuntu.

---

### Post by YesWeCan on 2011-08-22
Hi there. You may find it easiest to set up if you boot a live CD and use Disk Utility to format the drive with a Master Boot Record and make a partition at the end of the drive for Ubuntu and leave an unallocated space at the start for Windows.

I would make the partition for Ubuntu of type extended. Then you can later install Ubuntu entirely to logical partitions. This gives you maximum flexibility for future Windows installations.

After you've formatted the drive install Windows to the unallocted space. Afterwards install Ubuntu.

---

