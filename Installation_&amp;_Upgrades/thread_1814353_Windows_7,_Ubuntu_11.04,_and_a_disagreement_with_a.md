---
title: "Windows 7, Ubuntu 11.04, and a disagreement with a FAT32 partition"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by The_Third on 2011-07-29
I recently upgraded the 500GB HDD in my Sony Vaio VPCF2290X 2D to a 160GB SSD. I did this by shrinking the partitions on the 500GB HDD, creating the same partitions on the SSD and then using Clonezilla to transfer partition by partition to the SSD.
My system dual boots Windows 7 and Ubuntu 11.04. I made a FAT32 partition for the two OSes to share my music library. Ever since the transfer to the SSD, every time I access the FAT32 partition in Windows 7 then reboot in Ubuntu, Ubuntu has to fix the file system on the FAT32 partition before it can read or write to it without root privileges; every time I try to move a file to or from the partition as a non-root user before fixing it, I get a permission denied error. When I fix the partition file system in Ubuntu, it says it has to expand the file system to the entire partition and reclaim sectors. Attached are the details from the file system fix.
I'm suspicious that this has something to do with the alignment of my partitions on the SSD, and perhaps Windows 7 detects a discrepancy and fixes it but leaves it looking broken to Ubuntu. I do intend to realign the partitions on the SSD following advice from [here]("https://wiki.archlinux.org/index.php/Solid_State_Drives#Partition_Alignment"), but I need to wait for my new HDD enclosure to come in so that I can use my 500GB HDD to help out with that process; is there anything I can do to remedy the problem in the meantime? I do have a back up of my music library on another HDD so loss of data is not a concern.

EDIT: Forgot tot mention, the initial transfer from HDD to SSD was done using a borrowed enclosure that I had to return, no black magic was used in the process :p

---

