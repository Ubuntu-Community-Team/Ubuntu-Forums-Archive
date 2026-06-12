---
title: "after 11.10 install .error: no such device: 2112f..."
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by dancingLoki on 2011-11-18
after 11.10 USB install dual boot with win XP I get following:

error: no such device: 2112fcea-1a .....
grub rescue>

WTF?  I can still boot from USB, but can't boot to windows or the new ubuntu install.  I have no idea what to do now. Help!!!!!

---

### Post by BillyBoa on 2011-11-18
If you can reach the command line you can execute

```
sudo update-grub
```

---

### Post by BillyBoa on 2011-11-18
I copied what you have to do and reinstall grub:

Copy LiveCD Files
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods. If for example Windows is on sda1 and Ubuntu is on sda5, and Windows has overwritten the MBR, then the target for grub installation will be /dev/sda5, and the MBR in the boot sector of sda will be re written for grub.

This operation will write to the MBR and restore the modules and core.img to /boot/grub. It will not replace or restore grub.cfg or fix corrupted files.

Boot the LiveCD Desktop.
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".
sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
Mount the partition containing the Ubuntu installation.
sudo mount /dev/sdXY /mnt
Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot Note: If the user has a separate /home partition, this must be mounted to /mnt/home. Encrypted home partitions should work.
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
sudo grub-install --root-directory=/mnt /dev/sdX
Example: sudo grub-install --root-directory=/mnt /dev/sda
In Grub 1.99, introduced with Ubuntu 11.04, Natty Narwhal, a new switch is available which more clearly defines where the grub folder is placed. The command above will still work with Grub 1.99, but the following command is preferred by the developers. The target directory in the command is the command into which the grub folder will be installed. By default, and without the switch, the location is /boot/grub. In these instructions, since the Ubuntu partition is mounted on /mnt, the target would be /mnt/boot/grub.

sudo grub-install --boot-directory=/mnt/boot /dev/sdX
Example: sudo grub-install --boot-directory=/mnt/boot/ /dev/sda
Reboot
Refresh the GRUB 2 menu with sudo update-grub

---

