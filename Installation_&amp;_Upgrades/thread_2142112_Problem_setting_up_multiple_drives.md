---
title: "Problem setting up multiple drives"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by jonfromaustin on 2013-05-04
Hi,

I recently bought an old Dell T5400 to use as a home development machine I had an existing 750 gig drive and I bought an additional 128G ssd to hold the operating system. For the life of me I cannot seem to get it to work with both drives with the ssd as the boot drive. I think it may be in raid mode, but I'm not sure. Raid is not on in the bios, both drives are configured to use the RADI Autodetect/ATA option. I can't tell whether or not it's auto-detecting raid. 

- If I open the bios, I can choose to boot from the sata drives, but I cannot specify the drive priority. 
- The 750G drive is always listed as sata0. There are two sata plugs in the box labeled HDD0 and HDD1. Regardless which drive gets which plug, the HDD is always SATA0 and the SSD is always SATA1. From what I can tell, this causes the sytem to try and boot off the HDD. 
- I was able to install ubuntu 13.04 on the SSD, then add the HDD later and partition it. I set the SSD (sdb) as the boot drive. When I started up it went into grub rescue mode. My guess was it was trying to boot of the HDD (sda). 
- I ran the boot repair utility and i was not longer able to log into the system. There were some warnings about it being RAID, but everything seemed to work. When it restarted, I saw my user name, but my password no longer worked. Unplugging the HDD fixed the problem as I was then able to log in. My assumption here was that the HDD was now the boot drive - or something. I'm lost at this point.

I'd appreciate any help you guys could give me. Thanks.

---

### Post by oldfred on 2013-05-04
You need BIOS in AHCI or LBA, not RAID nor IDE.

If RAID present on drive then installer has issue unless you install server version.

If you are sure you do not what RAID, drives retain meta-data. This removes that:
 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

From Boot-Repair run the BootInfo script and post link it gives you.

Specs say some of those systems have hardware RAID, does yours? Then that may change things a lot.

---

