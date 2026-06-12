---
title: "Raid1 with 3 drives, 1 main with OS and 1 for file server (1 backup)"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Bauer17 on 2010-02-09
I am trying to do a new server install with Ubuntu server 9.10

I have 1 500MB drive that I was going to install the server software to.
Then (2) 1.5TB drives that I was going to use as a Home file server 1 with the data and 1 as a back up using raid1.

I am in the partition disk part of the install and have the following set up:

RAID1 device #0 - 1.5 TB - Software RAID device
  #1                         1.5TB            F            ext3      /  (not sure if I should change this to /home)

SCSI1 (0,1,0)  (sda) - 1.5TB ATA
   #1 primary              1.5TB    K raid

SCSI (0,0,0) (sbd) - 500.1 GB ATA
    #1 primary          494.1GB      F  ext3     /
   #5 logical             6.0GB           F swap     swap

SCSI (0,1,0)( (sdc)    - 1.5TB ATA
   #1 primary               1.5TB      K  raid

Then I try to finish partition and write changes to disk and I get the error:

"Identical mount points for two files systems
Two file systems are assigned the same mount point (/): RAID1 device #0 and SCSI (0,0,0), partition #1 (sbd)

please correct this by changing mount points."

Not sure what to change the mount point to on the RAID1 device, or if I have anything else wrong.  Any help would be greatly appreciated.

---

