---
title: "Wubi+NTFS problem"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by chandansomani on 2009-12-05
I was tryying to install Ubuntu 9.10 through wubi on Windows 7
but the error is 

>       [Linux-bzImage, setup=0x3400, size=0x3b26e0]
      [Initrd, addr=0x37a72000, size=0x57d098]

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/ouput error
NTFS is either inconsistent, or there is hardware fualt, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

Cannot mount /dev/sda1 on /isodevice

Tried chkdsk /f  ------- problem not yet solved

---

### Post by darkod on 2009-12-05
You are not running RAID are you?

Boot with the Ubuntu cd, select Try Ubuntu option and in terminal (Applications-Accessories) execute:
sudo apt-get remove dmraid

See if that helps to install wubi.exe after that.

---

