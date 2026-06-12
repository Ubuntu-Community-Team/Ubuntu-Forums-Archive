---
title: "Ubuntu 18.04.4 install Help + problem with installation"
date: 2020-03-20
forum: Installation &amp; Upgrades
---

### Post by nemes75 on 2020-03-20
I'm trying to install Ubuntu 18 on my [acer laptop]("https://www.acer.com/ac/en/GB/content/model/NT.LDREK.001")'s  internal disk. There is a factory-installed Windows 10 on it, so I tried to do a dual  boot, auto install with ubuntu + win10, but at the end of the install, I  was notified:
  The grub-efi-amd64-signed package could not be installed on target/
  I tried installing on the whole disk without dual boot. There I got  the same message. In the bios setup, I have disabled Secure Boot, and  have tried the steps recommended [here]("https://www.youtube.com/watch?v=VvmROT8LEsM"). The same error occurred.

---

### Post by yancek on 2020-03-20
I would suggest that you read the official Ubuntu documentation on dual booting with windows 10 UEFI at the link below and post back if you have specific problems/questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-03-20
In addtion, Acer has a unique requirement of setting "trust" in UEFI.
You have to have UEFI secure boot on & set a password to enable trust settings. Never lose password or reset when done.

All Acer seem to be very similar.
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by nemes75 on 2020-03-23
i have tried the different suggestions but end up grub could not be installed, it as if the emmc sd, the machine itself is locked, sp i tried to install on external sdd hard drive, i was also told that grub can not access disk 0 since it is locked and disk 0 is called mmcklb0 if i then format it to ext4 it is still called mmcklb0 ..

---

### Post by oldfred on 2020-03-23
Your MMC device is a device like sda or NVMe.
An install to an external drive still needs an ESP on the internal drive (your MMC), but you should have an ESP on the external drive, so you can reconfigure. The issue is Ubuntu's Ubiquity installer only installs to first drive, normally an internal drive.

You can create ESP on internal drive & copy entire thing to external drive. Normal boot would use ubuntu entry from internal drive's ESP. But UEFI boots from /EFI/Boot for all external devices & grub now create that also on internal drive. So copy of ESP to external drive would allow direct boot of external drive also. Or you can do the work around to force install to external drive's ESP.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

---

