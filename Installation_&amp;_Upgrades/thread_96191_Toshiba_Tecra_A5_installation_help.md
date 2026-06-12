---
title: "Toshiba Tecra A5 installation help"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by g-a-c on 2005-11-28
I have a Toshiba Tecra A5 laptop, with 60Gb disk and Windows XP. I want to dualboot Ubuntu Breezy onto it. I've split off 10Gb of the disk at the end and made it into an extended partition, booted from the Breezy ISO, but the installer doesn't show my disk info correctly.

When I get to the partitioning stage and choose the manual partitioning option, I just get a single entry for sda, and if I choose that option then it threatens to rewrite my partition table. My existing NTFS partition, and new free space partition are not visible.

The disk controller according to lspci from the install ISO is:
```
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
```I've tried searching the forums for "Tecra" "Tecra A5" and "Tecra sda" but couldn't find any useful results. Does anyone have one of these laptops and has successfully installed Ubuntu?

Note: there is also a Satellite Pro model which is very similar in hardware spec to the Tecra A5, but I can't remember the model number of it. Maybe someone has one of those?

---

### Post by g-a-c on 2005-11-30
I've now found the solution: when I used a Windows partition manager (Paragon Partition Manager 2005) to resize my NTFS partition and create an empty extended partition, it didn't seem to write the partition table correctly. 

I tried the Ubuntu install again and this time when I got to the disk section with the choices above, I went to the second terminal and ran fdisk from the command line. This warned me of the error, so I deleted the extended partition and created another.

The next time I tried the disk partitioning step, I could see the empty space as I expected and went on to do a successful installation.

---

