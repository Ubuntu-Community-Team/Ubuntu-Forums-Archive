---
title: "Dual Boot Windows 7 alongside Ubuntu 14.04 installed on Hybrid HDD"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by Prem_Reginald on 2015-04-01
Hi,

This is my first post on this forum. I have recently purchased a Dell Inspiron 15 5548. [HTML]http://www.dell.com/my/p/inspiron-15-5548-laptop/pd?oc=w511265myw8&model_id=inspiron-15-5548-laptop[/HTML] The model that I purchased came pre-installed with Ubuntu 14.04. I would like the dual-boot Windows 7 alongside with Ubuntu 14.04 (I don't mind removing the current installation of ubuntu if it is necessary).

Since the Ubuntu was installed on the 8GB Hybrid flash cache on the 1TB HDD, the flash cache is not displayed in my partition table. 

```
prem@prem-dell:~$ sudo parted --list[sudo] password for prem: 
Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition  boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition  hidden
 3      567MB   3789MB  3221MB  fat32           Basic data partition  msftdata
 4      3789MB  983GB   979GB   ext4
 5      983GB   1000GB  17.0GB  linux-swap(v1)



``` 

I have been searching for a tutorial on how to install Windows along-side Ubuntu but was only able to find the reverse. 

Please advise.

Thanks in advance.

---

### Post by yancek on 2015-04-01
The output you posted from the parted command shows a Linux partition (ext4 filesystem) of 979GB which is almost the entire drive.   First use GParted do shrink that partition to make room for windows.  You also have an EFI partition so I would expect Ubuntu is installed in EFI mode so you need to install windows 7 EFI also.  Or you could change to MBR and install windows 7 in MBR and then if you want to install Ubuntu, install it also in MBR.  Have you tried booting your windows 7 media yet and if so, what happens?

---

### Post by oldfred on 2015-04-01
Windows expects certain partitions, so best to let it create partitions in unallocated space.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

   Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by Prem_Reginald on 2015-04-01
Thanks yancek and oldfred. I will try it out and let you know.

oldfred: I would like to know, given the circumstances that i made a mistake and would like to re-create the partition table, how would I set the ubuntu to install into the 8GB flash cache?

---

### Post by oldfred on 2015-04-01
Is Ubuntu / (root) in cache? That is pretty small for /. I normally have 25GB allocated to / and use about 11GB of that including about 2GB for /home. But do have all data on hard drive.

I would full document system with Boot-Repair's Summary report. And save a copy of that to another device, DVD or flash drive. Then you know exactly how system is configured. Not sure the link to the paste bin last for more than a few months, so make sure you have a copy somewhere.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You should have current version repair tools for all installed systems. The installer for Ubuntu or repair CD/flash drive for Windows. You can add Boot-Repair easily to the Ubuntu installer.

---

