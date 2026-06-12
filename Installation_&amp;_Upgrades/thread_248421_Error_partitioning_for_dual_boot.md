---
title: "Error partitioning for dual boot"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by gbpacker on 2006-09-01
Hello,

I am trying to install dapper drake for dual boot with win-xp.
Here are the steps I followed:

1. started dapper drake from live cd
2. chose to install
3. select manual partition
4. made partitions for fat32, ext3 and swap
5. while applying the changes I am getting the following error:
error while resizing/moving /dev/sda1

My HDD is of type ST3250824AS  

Its serial ATA HDD with 7200 RPM. 

Can anyone tell me what could be the issue?

Thanks

---

### Post by goatflyer on 2006-09-01
It might be a problem writing the new partition sizes to MBR.  Your BIOS might have some kind of boot-sector anti-virus protection setting.  Go into BIOS menu and turn it off.

---

