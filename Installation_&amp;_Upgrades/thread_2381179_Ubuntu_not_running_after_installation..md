---
title: "Ubuntu not running after installation."
date: 2017-12-27
forum: Installation &amp; Upgrades
---

### Post by aadeniran on 2017-12-27
Hello everybody, I have had trouble getting Ubuntu to run on my computer.

I did boot repair using the recommended tab the result is here
[http://paste.ubuntu.com/26261449/](http://paste.ubuntu.com/26261449/)

After a successful boot repair, I was told not to forget to make my BIOS boot on mmcblkOp1/ubuntu/shimx64.efi file. How can I got about it?

I know that Ubuntu is installed on mmcblkOp1.

Currently, I have no windows operating system and assumed naturally ubuntu would run smoothly.


======this is where i set the boot to ubuntu============
ubuntu@ubuntu:~$ sudo efibootmgr -o 0004,0005,0001,2001,2002,2003
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0005,0001,2001,2002,2003
Boot0000* Unknown Device: 
Boot0001* USB HDD: KingstonDataTraveler 2.0
Boot0002* Unknown Device: 
Boot0003* Unknown Device: 
Boot0004* ubuntu
Boot0005* Linux
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
=========================================================
with that i restart the computer still no luck.
I used the USB boot medium and restart the computer before it goes to the boot medium  i took a  snapshot of what it said
"Fail to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load Image \EFI\BOOT\mmx64.efi: Not found
Failed to start Mock Manager: Not found."
if I go back to terminals immediately after restarting to check the boot order, changes to " BootOrder: 2001, 2002, 2003".

Now I thought to set the boot to a specific drive partition where Ubuntu was installed which is mmcblkOp1.
  using:   sudo fdisk -l                      ///I checked to confirm the all disk
then used this to set it: sudo fdisk /dev/mmcblk0     ///I entered m but never saw the "a" option.
///I entered p but just displayed that section on the drive
///Moreover there is no boot column for mmcblk0 unlike my USB boot drive /dev/sda
for mmcblk0=====================================
Device            Start      End  Sectors  Size Type
/dev/mmcblk0p1     2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2  1050624 57061375 56010752 26.7G Linux filesystem
/dev/mmcblk0p3 57061376 61077503  4016128  1.9G Linux swap
==============================End of mmcblk0========

For sda ==============================================
Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 60978815 60976768 29.1G  c W95 FAT32 (LBA)
=============================End of sda==================



I don't know what am doing wrong, I need help.

---

### Post by oldfred on 2017-12-27
If an Acer you need to set "trust" on the Ubuntu UEFI .efi boot files.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by aadeniran on 2017-12-28
Thank you very much I got it to work using the second link.

---

