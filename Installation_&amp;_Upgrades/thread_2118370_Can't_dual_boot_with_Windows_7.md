---
title: "Can't dual boot with Windows 7"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by fcogburn on 2013-02-21
Hello all, I have used Ubuntu before but it has been quite a while and I am very rusty. Never was very good at the inner workings of Ubuntu but enjoyed having an alternative to Windows. I am running Windows 7 Home Premium 64bit and have tried everything I know to try to dual boot with Ubuntu 12.10. I have an ssd as my main hard drive with a regular hd drive for storage. I have tried the Ubuntu windows installer, downloaded and burned a bootable Ubuntu 12.10 disk, checked the settings in my BIOS, everything I can think of to no avail. Would appreciate any help that can get me on the right path to dual booting Windows and Ubuntu again! Thanks so much in advance, all responses appreciated. Frank

---

### Post by carl4926 on 2013-02-21
SSD plus HDD
Is this machine using UEFI?

---

### Post by fcogburn on 2013-02-21
Thanks for your response. I really can't honestly say whether it is or not. There is an EFI setting in the BIOS but nothing about EUFI, sorry and thanks

---

### Post by carl4926 on 2013-02-21
EFI/UEFI = same

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2013-02-21
*Thread moved to **Installation & Upgrades**.*

You might also give 12.04 LTS a go and see if you get the same issues.

---

### Post by oldfred on 2013-02-22
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)


   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

   HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

