---
title: "Not getting option &quot;Normal installation&quot; when installing ubuntu 18 on Windows 10"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by rudai on 2020-04-03
Hi All,
I am trying to install dual-boot Ubuntu 18 from Windows 10 but I am getting error "need atleast 8 GB". This means that my hard disk is not being detected. Please help.
FYI, I have already disabled fast boot.

BIOS details:
SATA mode: Intel RST Premium with Intel Optane System accelaration
Intel RST 17.0.0.3720 RAID driver
Non-RAID physical disk: PCIe 1.0 IntelSSD ...

Physical DIsk info: 
Model: IntelSSD512GB
Status: Non-RAID
Controller type: NVMe
Controller interface: PCIe

Let me know if any other details are required to help me out.

Thanks in advance..

---

### Post by yancek on 2020-04-03
> I am getting error "need atleast 8 GB 

The message above indicates that you do not have a partition with a Linux filesystem equal to or larger than 8GB or that you do not have unallocated space available on the drive equal to or greater thatn that.
When you boot Ubuntu with the Try Ubuntu option and open a terminal and run the command:  sudo fdisk-l  does it show your partitions on the drive.  It would help someone to help you if you posted that output. 
If the command above does not show your partitions, then windows is still hibernated.  Turning that off is explained at the link below.  If that is not the problem, it is possible the problem is in regard to RAID which I know nothing about and can't help with.

[https://www.partitionwizard.com/partitionmagic/disable-hibernation-windows-10.html](https://www.partitionwizard.com/partitionmagic/disable-hibernation-windows-10.html)

---

### Post by rudai on 2020-04-03
Thanks Yancek for taking time to help me out!

**sudo fdisk-l:**
```
Disk /dev/sda: 3.8 GiB, 4041211904 bytes, 7892992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6e037a9d

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *        0 4153407 4153408    2G  0 Empty
/dev/sda2       12012   16939    4928  2.4M ef EFI (FAT-12/16/32)


Disk /dev/loop8: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
Since partitions are not recognized, I tried disabling hibernate, that also didnt help. 

Can someone help me in fixing the RAID issue?

---

### Post by Impavidus on 2020-04-03
> **rudai said:**
> 
BIOS details:
SATA mode: Intel RST Premium with Intel Optane System accelaration
Intel RST 17.0.0.3720 RAID driver
Non-RAID physical disk: PCIe 1.0 IntelSSD ...

I don't really know about Intel RST stuff, but this seems to be a problem. This thread may help: [https://ubuntuforums.org/showthread.php?t=2438824&highlight=Intel+RST](https://ubuntuforums.org/showthread.php?t=2438824&highlight=Intel+RST)

---

### Post by rudai on 2020-04-05
UPDATE: I could change SATA mode from Intel RST to AHCI, with which the partition was detectable and could install Ubuntu.. Great relief!
But now, Windows 10 is not booting up. Is the AHCI mode incompatible with Windows 10??

---

### Post by CelticWarrior on 2020-04-05
> **rudai said:**
> But now, Windows 10 is not booting up. Is the AHCI mode incompatible with Windows 10??

Someone show have told you that you should've installed AHCI support in Windows before changing the mode.

---

### Post by rudai on 2020-04-06
> **CelticWarrior said:**
> Someone show have told you that you should've installed AHCI support in Windows before changing the mode.

Oops!!! I wasn’t told to do so. Now, is there a way out?? Please let me know. Thanks in advance!!

---

### Post by CelticWarrior on 2020-04-06
Yes, there is.

Just change the mode back to what it was -> Windows will now boot; Ubuntu won't. Then boot Windows, install AHCI support (google for instructions) and after that change the mode to AHCI again and both should boot.

---

### Post by rudai on 2020-04-06
> **CelticWarrior said:**
> Yes, there is.

Just change the mode back to what it was -> Windows will now boot; Ubuntu won't. Then boot Windows, install AHCI support (google for instructions) and after that change the mode to AHCI again and both should boot.

Thanks CelticWarrior!!! Following the steps in link below, I could fix windows boot problem. Now I have both Windows and Ubuntu working!!! :) 
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

Thanks everyone!!!

---

### Post by CelticWarrior on 2020-04-06
You're welcome.

Please use the thread tool to mark it solved, thank you.

---

