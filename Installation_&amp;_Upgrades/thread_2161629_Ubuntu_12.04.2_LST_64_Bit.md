---
title: "Ubuntu 12.04.2 LST 64 Bit"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by gordie69 on 2013-07-11
Hey guys I'm dual booting with Ubuntu 12.04.2 LTS 64 bit and W7 only because I have a couple of things I still do with windows but getting to know more about ubuntu but I have W7 installed and I put my disk in to install along side W7 but at the prompt to decide that it only gives me the option of erase W7 and install 12.04 just wondering what happened if it was something I did or something missing.

---

### Post by prodigy_ on 2013-07-11
Well, either you don't have any free space left on the target drive or it has MBR partition table with all 4 primary partition "slots" already occupied. Either way you need to make room for another partition. Search the forum, there's a ton of threads on how to do that.

---

### Post by fantab on 2013-07-11
Ubuntu/Linux will NOT install on NTFS formatted partition or drive. 
Boot with Ubuntu DVD/USB and 'Try Ubuntu Without Installing". Let the desktop load. Now open Terminal [Ctrl+Alt+T] and run the following command:

```
sudo parted -l
```
and post its output here.

If you HDD has 'msdos' partition table (most likely it is) then you can have ONLY 4 Primary Partitions. Most of the OEMs utilize all 4 partitions. If you force a FIFTH then Windows will turn the 'Basic' disks into 'Dynamic' and that will be an issue. Linux will NOT boot from 'Dynamic' disks. To avoid this and to have more than 4 partitions we have to use Extended Partition which is not only a Primary Partition but also serves as a containter for LOGICAL Partitions. You will Probably have to create Logical Partitions. BUT first lets see the output of the above command.

---

