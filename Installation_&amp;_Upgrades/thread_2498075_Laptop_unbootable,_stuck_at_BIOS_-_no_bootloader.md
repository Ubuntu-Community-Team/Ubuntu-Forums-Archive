---
title: "Laptop unbootable, stuck at BIOS - no bootloader?"
date: 2024-05-29
forum: Installation &amp; Upgrades
---

### Post by pk1833 on 2024-05-29
Hi,


I lost the ability to access my Ubuntu/Windows installation after restarting my laptop today.

The laptop keeps entering BIOS and doesn't seem to recognize any boot loaders on the SSD. However, the most recent Live USB works nicely. I want to avoid doing a fresh install of Windows and Ubuntu if at all possible.

I've tried Boot-Repair from the Live USB and got this report:

[https://paste.ubuntu.com/p/m7tZMWRbT6/](https://paste.ubuntu.com/p/m7tZMWRbT6/)

Unfortunately, there is no repair button, but maybe I can get some help from you guys anyway.


Kind regards,
PK

---

### Post by oldfred on 2024-05-29
You are missing UEFI boot entries in UEFI?
Most systems, I thought found a Windows entry if files are in ESP - efi system partition.
You seem to have both the /EFI/Microsoft & /EFI/ubuntu folders in ESP for UEFI boot.
But your p6 seems to be corrupted.

I might try adding a Windows UEFI boot entry from live installer. And run fsck on p6 to see it that repairs p6. If that works then you can add UEFI boot entry for Ubuntu with Boot-Repair's advanced mode (full reinstall of grub) or manually with just efibootmgr.

Windows boot entry using efibootmgr.
This should create a new entry, since nvme drive may need detailed entry that specifies drive & partition:
sudo efibootmgr -c  -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvvme0n1 -p 1
See also:
man efibootmgr
Check that entry is added.
sudo efibootmgr -v

#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
sudo e2fsck -f -y -v /dev/nvme0n1p6

Ubuntu UEFI entry if everything else is ok, otherwise full reinstall of grub may be required.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvvme0n1 -p 1

---

### Post by pk1833 on 2024-05-30
Many thanks oldfred for coming back to me,

I thought I'd start with working out whether the /dev/nvme0n1p6 can be 'repaired' or not.

I've tried both commands, but it's failing for me on:

/dev/nvme0n1p6: recovering journal
e2fsck: Input/output error while recovering journal of /dev/nvme0n1p6
e2fsck: unable to set superblock flags on /dev/nvme0n1p6
  
/dev/nvme0n1p6: ********** WARNING: Filesystem still has errors **********

The second command does not show the e2fsck: Input/output error while recovering journal of /dev/nvme0n1p6 error, but otherwise it's all the same.

I wonder how likely am I facing a hardware issue with the SSD? If there is a way to confirm this theory, then I'd rather have someone look at my laptop instead of spending hours/days trying to make it bootable just to see another failure.

Thanks,

---

### Post by oldfred on 2024-05-30
Do you have good backups?
SSDs do not last forever, and may just fail suddenly. 

You can check drive status. Change examples with /dev/sda to /dev/nvme0n1 for NVMe drives.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
If not Ubuntu but other flavor, you can install it.
sudo apt-get update -y
sudo apt-get install -y gnome-disk-utility
Smart Data 
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)
sudo apt-get install smartmontools
sudo parted -l ## to identify the internal harddrive, here shown as 'sda'
sudo smartctl -t long /dev/sda
sudo smartctl -a -d ata /dev/sda ## To display detailed SMART information

---

### Post by tea for one on 2024-05-30
[https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)
This info may help with superblock problem.

As mentioned by oldfred, backups are your safety belt.

---

