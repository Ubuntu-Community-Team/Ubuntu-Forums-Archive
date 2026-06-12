---
title: "GParted Anomaly: fat32 partition shows 27 GB used just after formatting"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by Pratik Ali on 2010-03-17
I formatted 56 GBs of my hard disk space into fat32 and it seems that 27 gbs of it is used! Though direct checking from the volume itself shows nothing like this, gparted still insists 27 gbs are used.

any ideas why?

---

### Post by louieb on 2010-03-17
IIRC - fat32 has a 33GB or so maximum partition size limit. [http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm) 

Looked around a bit seems [http://www.ntfs.com/ntfs_vs_fat.htm]("http://www.ntfs.com/ntfs_vs_fat.htmn") WIN98 could format  up to a 127GB fat partition. But win 2000 and later 32 GB was the max. Google is your friend.

---

### Post by oldfred on 2010-03-17
I do not recommend using FAT except for USB type devices where they have to be FAT. 

FAT has a maximum of 4GB file size so any video or backup that exceeds that size will not be saved correctly. FAT also so not have journaling so recovery from errors is more difficult.

I would suggest NTFS if you need compatibility with windows. Otherwise EXT3 or EXT4 for Ubuntu.

---

### Post by coffeecat on 2010-03-17
> **louieb said:**
> IIRC - fat32 has a 33GB or so maximum partition size limit. [http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm) 

Looked around a bit seems [http://www.ntfs.com/ntfs_vs_fat.htm]("http://www.ntfs.com/ntfs_vs_fat.htmn") WIN98 could format  up to a 127GB fat partition. But win 2000 and later 32 GB was the max. Google is your friend.

Google might be your friend, but I find wikipedia to be quite friendly too. :wink: [Linky]("http://en.wikipedia.org/wiki/Fat32#FAT32"). 

> The Windows 2000/XP installation program and filesystem creation tool imposes a limitation of 32 GB_._ **However, both systems can read and write to FAT32 file systems of any size.** This limitation is by design and according to Microsoft was imposed because many tasks on a very large FAT32 file system become slow and inefficient. **This limitation can be bypassed by using third-party formatting utilities. ** Windows Me supports the FAT32 file system without any limits.
I have successfully formatted a 320GB drive with one single FAT32 partition which was usable in Windows, using Gparted. And I regularly use a 60GB FAT32 USB drive formatted in Gparted and used for transferring file between Ubuntu, MacOS and Windows. But Microsoft has a point. Huge FAT32 partitions are not a good idea. 

@Pratik Ali, I can't answer your question. I've never seen that. You could try reformatting it in case something went wrong with the format. Or you could try NTFS, but only if you have Windows available for if the NTFS filesystem needs repairing. Or, as oldfred suggests, use ext3/4.

---

### Post by Grenage on 2010-03-17
Indeed.  Most Hard Disk recorders operate on FAT32 (at least those I have seen), so I often create FAT32 partitions in excess of 500GB.

---

