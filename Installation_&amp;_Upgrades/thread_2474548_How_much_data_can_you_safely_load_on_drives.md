---
title: "How much data can you safely load on drives?"
date: 2022-05-02
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2022-05-02
Heard in the past it was best to load mechanical HDDs to about 80% capacity. Was told HDDs can start to act funny and have performance issues when you fill them up further say 90% or more.

Does this still apply to SSDs and Flashdrives today? I still apply that 80% rule to SSDs but wonder if it applies to Flashdrives? For example I use 32GB and 64GB thumbdrives with mp3 music files for my stereo and vehicles and can easily load these flashdrives up to full capacity. Is this OK or not?

---

### Post by cybrsaylr on 2022-05-04
Bump

Anyone have any thoughts on this?

---

### Post by #&amp;thj^% on 2022-05-04
Once I loaded my WD SSD to 10% free noticed a little hit.
 Only write speeds would be affected., moved some stuff over to a backup drive,  back to normal.
Not all SSD's are the samr though, So even if you don't do overprovisioning there's already ~10% reserved space on the drive. 
[https://www.seagate.com/ca/en/tech-insights/ssd-over-provisioning-benefits-master-ti/](https://www.seagate.com/ca/en/tech-insights/ssd-over-provisioning-benefits-master-ti/)

[https://www.pcgamer.com/why-you-dont-get-the-capacity-on-your-ssd-the-packaging-claims/](https://www.pcgamer.com/why-you-dont-get-the-capacity-on-your-ssd-the-packaging-claims/)

TRIM, however, is essential for keeping your SSD in tip-top shape.

When writing data, the SSD can write only to empty sectors. This means if an SSD needs to modify a filled sector, it has to read it, note the contents, modify them, erase the sector, and write the modified contents. If we wanted to overwrite a sector, we&#8217;d have to erase the sector and write the new contents to the now-empty sector. The extra steps take time.

Operating systems typically just delete a file by marking its data on the disk as deleted and erasing the pointer to it. The file&#8217;s data is still there on the disk, but it will be overwritten only when the operating system needs that &#8220;empty&#8221; space to write new files to the disk.

The TRIM command tells the SSD to erase and consolidate cells that are no longer in use, so writing to those sectors in the future will be just as fast as when the drive was new. If not for TRIM, writes would take longer, and an SSD&#8217;s performance would deteriorate as you filled it up and deleted files from it.

---

### Post by ubfan1 on 2022-05-04
Further thoughts on TRIM:  If you stick an SSD into an external USB  enclosure, you may lose the TRIM capability.  eSATA enclosures work fine.

---

### Post by cybrsaylr on 2022-05-05
OK so that takes care of SSDs.

How about Flash drives? I have filled a couple up completely with mp3 files to use in my car and at home. So far seem to have no issues. Just wondering if this is ok?

---

### Post by #&amp;thj^% on 2022-05-05
Largely depends on the flash drive brand, and i too fill mine 80-90% full. (I mainly use them for tools)
All mine are about 4-7 years old now.

---

### Post by grahammechanical on 2022-05-05
There is something to keep in mind if using an ssd with Ubuntu on the ssd. The latest versions of Ubuntu use a swap file which is variable in size and not a fixed size swap partition. I guess that if the ssd gets close to being full it might constrict the resizing of the swap file to meet the needs of the OS. A lot will depend upon how much memory is being used and whether multiple large files are being accessed.

Regards

---

### Post by vanadium on 2022-05-06
> **grahammechanical said:**
> The latest versions of Ubuntu use a swap file which is variable in size and not a fixed size swap partition.
That is, afaik, not correct. Swap files are not dynamically sized, also not in U 22.04.

I see no issue with close to full drives if this is largely static content, i.e. archive data, etc. For dynamic disks, little free space will lead to fragmentation. This hits performance for traditional drives, not as much for SSD drives. For SSD drives, it has been mentionned: the performance hit will be in the need of the system to discard almost every time, unless you trim very frequently - which also needs time.

---

