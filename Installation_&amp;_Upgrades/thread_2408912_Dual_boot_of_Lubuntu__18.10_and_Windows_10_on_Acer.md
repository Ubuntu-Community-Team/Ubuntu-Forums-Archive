---
title: "Dual boot of Lubuntu  18.10 and Windows 10 on Acer One 10"
date: 2018-12-25
forum: Installation &amp; Upgrades
---

### Post by ubtnk on 2018-12-25
For the reason of weight (2.8 lbs), I'd like to buy Acer One 10.
1. Is the installation of Lubuntu for dual boot of Lubuntu 18.10 and pre-installed Windows 10 difficult?
2. Is Acer One 10 suitable for Ubuntu 18.04 to dual boot with Windows 10 ?

---

### Post by oldfred on 2018-12-25
What model, and is this an older used, I do not find specs for any current verisons.

The MMC card of 32GB makes it just about impossible to dual boot. You may be able to install to an external flash card and boot it?
And some only have 1GB of RAM which is now very small.

See another older thread on lightweight Acer.
[https://ubuntuforums.org/showthread.php?t=2256083](https://ubuntuforums.org/showthread.php?t=2256083)

---

### Post by ubtnk on 2018-12-25
It is Acer Switch One 10 SW110 - 4 Gb RAM - 32 Gb eMMC.

---

### Post by yancek on 2018-12-25
If microsoft is to be believed, you will have a very difficult time installing it based on space requirements.  See the link to the microsoft site below.  You could boot your Linux DVD/USB and run sudo parted -l to list partitions and space used/available.

[https://www.microsoft.com/en-ie/windows/windows-10-specifications#primaryR2](https://www.microsoft.com/en-ie/windows/windows-10-specifications#primaryR2)

---

### Post by oldfred on 2018-12-25
It looks like one of those systems that is 64 bit, but uses a 32 bit UEFI for some odd reason?

       Acer switch 32 bit bootia32.efi
[https://askubuntu.com/questions/1040519/installing-32bit-bootloader-on-64bit-ubuntu-solved](https://askubuntu.com/questions/1040519/installing-32bit-bootloader-on-64bit-ubuntu-solved)

---

