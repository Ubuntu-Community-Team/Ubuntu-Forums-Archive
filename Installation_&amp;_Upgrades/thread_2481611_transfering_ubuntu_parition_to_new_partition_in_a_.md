---
title: "transfering ubuntu parition to new partition in a new drive"
date: 2022-12-04
forum: Installation &amp; Upgrades
---

### Post by shome on 2022-12-04
I had a dual boot SSD with windows7 (on primary) and ubuntu 18.04 (on extended partition). I needed to delete the windows partition so as to let ubuntu use the entire HDD. Since ubuntu was on extended partition, it was not possible to resize it. So, I created an image of the ubuntu 18.04 partition using clonezilla. Then, I deleted all the existing partitions in the SSD and created a single new ext4 partition on the SSD (sda1). Next I cloned the 18.04 partition image back to the new partition (sda1). However, I got an error message stating that it was unable to restore extended boot record into an extended partition (sda4) which existed in the SSD before creating the new partition table. I tried to use disk repair to fix the boot issue, but it failed to do so.

**My question is [B]how to create a bootable ubuntu disk (in a newly formatted/partitioned SSD/HDD) from an image of an ubuntu partition**?[/B]

---

### Post by tea for one on 2022-12-05
I would doubt if you can install and boot this Clonezilla image because:-
[LIST]
[*]It was created from an extended partition and the Master Boot Record is missing.
[*]All the original partitions have now been deleted.[/LIST]
Before going any further, do you have a personal data backup other than this Clonezilla image?
If you do, then install Ubuntu LTS and restore your backup.

If not, briefly, the procedure would be:-
Install an LTS version of Ubuntu in UEFI mode with GPT.
The installer will automatically create two partitions but you will need three.
During the installation, create a third partition large enough to accept your extracted Clonezilla image.

Boot into your new Ubuntu OS and check that you are comfortable with the newer system.
Boot into a Clonezilla session and extact your image to the third (unused) partition.

Boot into your new Ubuntu LTS OS and copy the personal data you need to your new home directory.

---

### Post by oldfred on 2022-12-05
Windows 7 systems were mostly BIOS with MBR(msdos) partitioning. A few just before Windows 8 were UEFI with gpt partitioning.
Microsoft required UEFI boot with gpt partitioning in 2012 with release of Windows 8. Or 10 years ago.

I started converting drives to gpt about 2010 with my BIOS only system. And have not created a new MBR drive since.
Every  new or totally redone drive was converted to gpt, so by the time I had an UEFI system all drives were gpt.

I also believe in new installs, and restore from your backup. Becomes good test that your backup is complete as you still have old drive to find something missing. When drive fails you will not have that chance & backup must be complete.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

