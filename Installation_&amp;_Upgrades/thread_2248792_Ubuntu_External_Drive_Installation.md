---
title: "Ubuntu External Drive Installation"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by darb78 on 2014-10-17
I successfully installed Ubuntu 12.04 to an external 1TB drive. I set-aside about 1/3 of it for the system. I would like to set the other 2/3 up as a traditional USB drive that I can use with my macs as well as when I'm running Ubuntu. I've dug around but can't see to figure out how to make this happen. Thanks in advance!

---

### Post by mikewhatever on 2014-10-17
You probably need to format it with my macs. What's in the "other 2/3" now? Unallocated space? A partition? My macs should be able to see a partition, I assume.

---

### Post by darb78 on 2014-10-18
Ok, I used my mac to format the drive as ExtFat to start and Ubuntu wouldn't recognize the drive. I changed the formatting to Mac Extended and now I can no longer use the hard drive to boot the computer. When I start the computer with the extra drive attached and hold down the Option key it fails to recognize that there is a drive attached. I have tried changing the disk format, however regardless of the formatting type the computer still fails to recognize it. Thoughts on how I can fix this without reinstalling?

---

### Post by Vladlenin5000 on 2014-10-18
Whatever you do leave the partitions where Ubuntu has been installed alone, never touch them. Otherwise it won't boot, obviously. You should partition and format the remaining of the drive only, according to your needs.
If you formated the whole drive then you just deleted Ubuntu.

---

### Post by oldfred on 2014-10-18
Mac uses gpt partitioning?
Did you install Ubuntu with gpt partitioning?, default is usually MBR(msdos).

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Ubuntu will boot with either UEFI or BIOS from gpt partitioned drives. And Windows since Vista will read gpt data drives, but Windows only boots from gpt drives with UEFI.

You do not want hybrid drive:
      
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

