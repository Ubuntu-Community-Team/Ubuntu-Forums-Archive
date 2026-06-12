---
title: "install os on external SSD to boot on any computer"
date: 2019-03-13
forum: Installation &amp; Upgrades
---

### Post by xaivic on 2019-03-13
Hi im new to linux based OS and i want to install several OS on an external SSD to boot from any computer just like you can do on a USB drive.
I have a spare SSD and a docking station for it that i carry with me when help people with their computers and it would have faster write/read then if i would buy a cheap usb stick.
been trying to look for any guides on the matter but it all seems to be intended to be used on the same system it is installed on.
would be extremely thankful if someone can help me.

---

### Post by oldfred on 2019-03-13
UEFI or BIOS? Microsoft has required UEFI since release of Windows 8 inb 2012, but users can install in either mode.
Bit more difficult to have both with one system. 
I just use different flash drives, one with full install of Ubuntu in BIOS mode, and most now UEFI configured, since I have not had a BIOS system for a few years.

BIOS is easier to configure as during install you use Something Else and install grub boot loader to external drive.

But with UEFI, you have to partition in advance to include an ESP - efi system partition (FAT32). But the selection to install grub2's boot loader to external does not work. I just tried again with 19.04 to see if grub updates improved it. During install it will say it is installing to external, but it does not. My work around is to then copy /EFI/ubuntu from internal drive's ESP to ESP on external twice. Second time to /EFI/Boot and rename bootx64.efi to shimx64.efi. UEFI only boots external drives from /EFI/Boot/bootx64.efi. (same files for both Windows & Ubuntu installers, but obviously different actual files.)

I also include multiple repair ISO on my external drives and boot them with grub's loopmount commands.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Ubuntu now uses swap file, so no swap partition required. Default install is just / (root) and if UEFI, the ESP. But I prefer to separate / from my data. New users often then have separate /home partition, more advanced users may want data partition(s).
       
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

For new users disconnecting internal drive, either physically or in UEFI settings will force Ubuntu to correctly install to only drive including correctly configured ESP is the most simple way.

 **Two Drive UEFI installs **- same instructions whether internal or external
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
[http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/)
HP Envy 13 install to external drive
[https://ubuntuforums.org/showthread.php?t=2413599](https://ubuntuforums.org/showthread.php?t=2413599)
Uses rEFInd on HP with 2 drives
[http://askubuntu.com/questions/721867/dual-boot-ubuntu-14-04-3-lts-with-win-10-on-separate-hard-drives](http://askubuntu.com/questions/721867/dual-boot-ubuntu-14-04-3-lts-with-win-10-on-separate-hard-drives)
Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot](http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot)
[http://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147](http://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147)
hide sda so second drive seen as sda
[http://askubuntu.com/questions/797989/ubiquity-mounts-wrong-esp-during-install](http://askubuntu.com/questions/797989/ubiquity-mounts-wrong-esp-during-install)
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)

---

### Post by C.S.Cameron on 2019-03-14
[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577) 
Will work on SSD as well as flash drive.
Also see:
[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812)

---

