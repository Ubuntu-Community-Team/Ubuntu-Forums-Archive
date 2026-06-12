---
title: "Grub doesn't find windows"
date: 2020-04-08
forum: Installation &amp; Upgrades
---

### Post by naib864 on 2020-04-08
I reinstalled my Ubuntu dual boot and now the grub won't find windows anymore. I already ran boot repair and tried to manually add windows into the grub config.
The grub won't show up on startup and when I summon it manually, the option added for Windows doesn't work.
I think I added the wrong drive, or maybe the mbr is broken. But how do I fix that?

This is the windows drive:
[ATTACH=CONFIG]285461[/ATTACH]

EDIT:

I'm not sure which one to add as windows? Both sdb1 and sdb2 didn't work.
I added this entry to the grub with the respective uuid:

insmod ntfs
search --no-floppy --set=root --fs-uuid $$UUID$$

---

### Post by CelticWarrior on 2020-04-08
The typical cause for that is OSes installed in different modes and/or Windows "hibernated" due to the Fast Startup feature.
Boot Repair won't solve either but what Boot Repair can do is to produce a summary report that shows what's happening. Please do it and post it here.

---

### Post by naib864 on 2020-04-08
[https://paste.ubuntu.com/p/kYtFbSFWf9/](https://paste.ubuntu.com/p/kYtFbSFWf9/)

---

### Post by oldfred on 2020-04-08
It looks like you have a new UEFI system with a NVMe drive.
But have Windows installed in BIOS boot mode to MBR drive.
Windows only installs in BIOS mode to MBR drives and only installs in UEFI mode to gpt partitioned drives.

But it also looks like you have Ubuntu installed in UEFI boot mode on the old MBR partitioning with new NVMe drive. Real mix of old configuration on new system.

But UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch. Or grub can only boot other installs in same boot mode.
You can convert Ubuntu UEFI to BIOS by booting Ubuntu live installer in BIOS mode, add Boot-Repair and install grub to MBR of NVMe drive. Do NOT run auto fix as that installs grub to MBR of all drives and you want the Windows boot loader on the Windows drive.

You probably need to reinstall BIOS Windows boot loader to sdc. Boot-Repair's advanced mode lets you choose one operating system and one drive to install boot loader. For BIOS it can install syslinux boot loader to boot Windows. 
Otherwise you have to use your Windows repair/recovery drive to run Windows fixes.

---

### Post by naib864 on 2020-04-09
> **oldfred said:**
> 
You can convert Ubuntu UEFI to BIOS by booting Ubuntu live installer in BIOS mode


How do I choose which mode to boot the Live-USB in?

EDIT: Found it, will update this post if I run into further problems.

EDIT 2: Boot repair info in advance: [https://paste.ubuntu.com/p/vd9zCBq5JN/](https://paste.ubuntu.com/p/vd9zCBq5JN/)

EDIT 3: Ubuntu is still in UEFI-Mode even though I installed the legacy GRUB...

---

### Post by oldfred on 2020-04-09
Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

Report did not show fstab?
Install of BIOS version of grub should have commented out (with #) any mounts of the ESP.
cat /etc/fstab

---

### Post by naib864 on 2020-04-09
Yeah it's still UEFI mode. But I booted the Live-USB in BIOS mode, I even checked it before running boot repair.

fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=ee41c928-2cfe-47d6-a16a-a0720209af0c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
#UUID=7BD6-50EE  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

---

### Post by oldfred on 2020-04-09
That shows ESP commented out, so grub-pc installed for CSM boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by naib864 on 2020-04-09
Alright, so I have no idea how it works but I switched the boot drive from the nvme drive to my ssd where windows is installed on.
Now the grub is showing and everything works fine.

---

