---
title: "Ubiquity not listing my SSD"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by daniel232 on 2014-12-18
Hello,

I am trying to install onto /dev/sda2 which is an 80G SSD. when I get to disk setup, I switch to manual and hit continue. No /dev/sda devices are listed. There are no errors related to the drives in dmesg.

fdisk -l returns
Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a3feeda

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 115343359 115341312   55G  7 HPFS/NTFS/exFAT
/dev/sda2       115346700 156296384  40949685 19.5G 83 Linux

I can mount both partitions without problems as well. 
I have tried booting with nodmraid option. 

Running dmraid -E -r /dev/sda returns
Do you really want to erase "ddf1" ondisk metadata on /dev/sda ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sda" to 40973497008128
ERROR: writing metadata to /dev/sda, offset 80026361344 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda

Running ubiquity --debug I noticed a dmraid.ddf1 directory being created with sda.* files in it.

I have tried setting my bios to AHCI and Enhanced IDE. As far as I can tell I cannot prevent that drive from being detected as raid.

Suggestions on what I should try next?

Thank you.

---

### Post by oldfred on 2014-12-18
Was this drive part of a RAID configuration before? You may need what ever ondisk proprietary tools are to clear it? Or do you have a proprietary controller in your system?

Not familiar with ondisk but usually the dmraid command clears the meta-data.
If nothing else write zeros to entire drive with shred or dd? But be very careful if you use dd.

Once you get it cleared you do need drive in AHCI mode.

---

### Post by daniel232 on 2014-12-23
Thanks for the reply. I never did have the drive in a raid array but it was attached to a raid controller a while back. I managed to fix the problem by booting into my raid management console. However the stupid thing nuked my partition table which held both Windows and Linux. I even pressed N when it asked me to confirm the action because that set off alarm bells. Anyways, took me a few days to restore the table but I am up and running again.

---

