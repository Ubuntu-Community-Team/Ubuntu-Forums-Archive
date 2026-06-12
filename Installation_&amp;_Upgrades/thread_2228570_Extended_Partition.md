---
title: "Extended Partition?"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by echotech2 on 2014-06-08
I just installed 14.04 form the LiveCd on a brand new SSD.  I formatted the SSD to ext4 (for no particular reson), then removed the original HD and booted from the LiveCD.   I chose install and "erase and use entire disk". All went well, works fine from SSD.

  My question is: This method created the normal SDA1 and also a 4Gb extended partition with a 4Gb swap file SDA5.  Is there a reason for creating an extended partition and putting swap in it or is that "just the way it is done"?

```
dave@dave:~$ blkid
/dev/sda1: UUID="7946a634-4e49-4526-b1b5-51af7b21c907" TYPE="ext4" 
/dev/sda5: UUID="bdb527f0-2635-487d-ae61-868e16212737" TYPE="swap"
```

  No harm done but I am just curious.

  --Dave

---

### Post by MrSteve on 2014-06-08
that's the way the auto set-up works for partitioning 

i use a simple manual set-up
20GB / (root) primary ext4
2GB /swap extended
rest of HDD /home extended ext4

this way i can install/replace/upgrade the system and have/leave the /home partition intact ...

---

### Post by oldfred on 2014-06-08
That is the way it is done, as with somewhat larger drive you may want an extended partition to allow more than the limited 4 primary partitions.

But if only installing Linux not Windows, there are some advantages to gpt partitioning.
And I only have a BIOS system but hope to build a new UEFI system, so I have partitioned all new drives for the last couple of years (including flash) with gpt and include an efi partition for future use with UEFI and a bios_grub to boot in BIOS mode now.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 but without journel since partition is small, I use a daily cron task for trim, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by echotech2 on 2014-06-09
Thanks for the info.  This is an old machine, the BIOS is dated 2002-2006, so none of that fancy UEFI or GPT stuff. My friendly computer shop guy was surprised this computer even recognized the SSD, he's seen some that won't. 

BTW,   I'm 69 (that's years old...) and a lot of my computer knowledge comes from my 13-year-old niece.

---

### Post by oldfred on 2014-06-09
Parts of my system are from 2006, but I updated motherboard & video card in 2009. 
You need to have an AHCI setting in BIOS for the SSD for trim to work.

I am not **that** old, at least a year younger than you. :)
Grandson is only 2 and MrsOldfred has him swiping to see new pictures (of him mostly) on the iPad.

---

