---
title: "Ubuntu Server 18 on RAID 1 UEFI won't boot after copying EFI partition"
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by leonv12 on 2019-12-04
On past versions of Ubuntu Server, I have successfully installed to a raid 1 with "https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios" or similar without any problems.  I could boot from either drive, but not with 18.04.

My config is two 4TB drives (and this same config worked fine on previous versions)
sda1 and sdb1     1G      efi (bootable)
sda2 and sdb2     10G    raid to md0 as swap swap
sda3 and sdb3     50G    raid to ext4-md1 mounts to /
sda4 and sdb4     Remainder    raid to ext4-md2 mounts to /data

On past versions, after install, I verify the active efi and copy the efi partition to the second drive and all was well. I could boot from either drive and recover a failed drive in the raid 1.

On 18.04 (using the alternate) after I copy the efi, the boot goes to the grub prompt.  If I force to the other drive, i get insert bootable device...

Ideas? Suggestions?

Thank You!!!

---

### Post by oldfred on 2019-12-05
Do not know server and this only runs from system with gui/desktop.
If you have Ubuntu live installer for desktop or can get it. 

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

