---
title: "How to dual-boot an Ubuntu / Windows new Acer Aspire machine?"
date: 2021-02-01
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2021-02-01
I am thinking of buying a Acer Aspire 5 with Windows 10 Home. I'd like to set up a dual boot with the majority of the hard drive dedicated to Ubuntu 20.04. 

There are a few threads about Acer machines but many are several years old. Is there an up-to-date guide? 

Some threads say that "trust" (not entirely sure what that is) must be set in the UEFI. Is there anything else that needs to be assigned?

Thanks.

---

### Post by yancek on 2021-02-01
The official Ubuntu documentation on dual booting with windows 10 is at the link below.  Read it thoroughly before beginning.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Newer Acer computers require that trust be set in the BIOS firmware before you can install an operating system other than windows.  Before you can do this, you need to set a Supervisor password in your BIOS firmware.  Some info on that at the link below.

[https://community.acer.com/en/discussion/538305/cant-access-uefi-after-installing-linux-dual-boot/p1](https://community.acer.com/en/discussion/538305/cant-access-uefi-after-installing-linux-dual-boot/p1)

---

### Post by oldfred on 2021-02-01
Some Acer threads.
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by ActionParsnip on 2021-02-01
Resize NTFS in Windows. You'll want about 30Gb or more for Ubuntu. You can then boot to the install media and install Ubuntu to the new freed space

---

### Post by Bobby_James on 2021-02-01
Thanks to all - I understand this rather more now. 

Is it best to create the new partition in Windows 10 or to create it when using the Ubuntu USB? And is the type ext4 or NTFS something else?

---

### Post by oldfred on 2021-02-01
Generally you use Windows tools for Windows & Linux tools for Linux.
Or from Windows you cannot create Linux partitions.
But should use Windows to shrink NTFS partitions. And immediately reboot, so it can run required chkdsk.

Linux partitions must be Linux formatted, ext4 is most common, but others are available.
Windows NTFS or FAT32 do not support Linux ownership & permissions. But Linux has drivers to read & write NTFS partitions, if Windows hibernation is off. Windows fast start up also sets hibernation flag so it must also be off.

UEFI does use a FAT32 partition for boot files. Typically Windows & Ubuntu share one ESP - efi system partition on first drive. Only one per drive.
More details in link in my signature below.

---

### Post by Bobby_James on 2021-02-02
Right, so I shrink the NTFS partition in Windows 10, thus creating the free space for an ext4 partition when installing Ubuntu from the flash memory.

My impression is I use the "Disk Management" tool, then select a large volume, then use "Shrink Volume".

---

### Post by yancek on 2021-02-02
>  My impression is I use the "Disk Management" tool, then select a large volume, then use "Shrink Volume". 		

Yes, use Disk Management and generally shrink the largest partition and free 20-30GB for Ubuntu.  When you boot the Ubuntu installer you can either create partitions for Ubuntu in the installer or use GParted which is part of the install DVD/USB and do it prior to beginning the install.

---

