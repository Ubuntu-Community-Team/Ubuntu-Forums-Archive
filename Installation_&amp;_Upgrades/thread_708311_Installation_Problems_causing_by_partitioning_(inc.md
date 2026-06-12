---
title: "Installation Problems causing by partitioning (incl. GParted Crash!)"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by simon_x on 2008-02-26
Hi Helpers,

I have some weird problem, i hope you can help me with.

Firstly the Hardware:

ASUS A3G Notebook ( Pentium M 1,6 GHz, 1 GB RAM, 40GB HDD )

Secondly the partition situation at the moment:

1st Partition is a 10GB primary NTFS Partition having WindowsXP installed
2nd Partition is a 20GB secondary NTFS Partition beeing a data storage
3rd is a section of 10GB unformatted free space

Thirdly description of the Problem:

I want to install ubuntu 7.10 from the LiveCD. I had some very early version of Ubuntu installed before but didn't use it.. the 10 GB free space was a former ReiserFS partition with that system on. So i deleted the partition in Order to install 7.10 completely new.

Okay, after booting from the LiveCD i start GParted to create the partition and the swap for the install.
**BUT** GParted detects a 40GB unformatted harddisk. The other partitions are not visible. Same thing in the Ubuntu Installtool. The weird thing is, that both NTFS partitions can be mounted and the GNome Filebrowser can display their files. Switching back to Gparted after this causes a complete crash of GParted.

I can mount and unmount the partitions but this doesn't help.

No chance of partitioning my hdd the way i want.

Weird thing, hm?
I would be delighted if you could help me!

Greetings
Simon

---

### Post by logos34 on 2008-02-26
Try**TestDisk** to recover/fix partition table:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection)

Use with caution.  Backup your files!

---

