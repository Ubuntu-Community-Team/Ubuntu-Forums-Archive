---
title: "Dual boot on external hard drives / Ubuntu 16.04.2 LTS &amp; Windows 7"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by mrpaskal on 2017-04-11
Hi guys ! I'm looking to make a dual boot between Windows 7 and Ubuntu 16.04.2. I have Windows 7 installed on my internal hard drive but I wanted to use an external hard drive to install Ubuntu. I'm wondering which partition I need to mount. 

I've looked on the web and I found out some people recommand to install :
/ (ext4) 
/ swap
/ boot

Is it correct ? Is there anything else I need ? 

Thanks !

---

### Post by Dennis N on 2017-04-11
Assuming this is not a UEFI install, all you need is a root partition and swap partition. The only need for a separate boot partition is when you choose an LVM install.

---

### Post by oldfred on 2017-04-11
You do need to use Something Else so you have the option on the partitioning screen to install the grub2 bootloader to the external drive. You want to keep the Windows boot loader on the internal drive. And set BIOS to boot from external drive first, internal second. Grub will give you the option to boot Windows or Ubuntu, and if you unplug external then BIOS will boot external. If grub on external and you unplug that drive, you cannot boot as grub in MBR needs the rest of grub in external drive.

       MBR or gpt partitions:
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 


Most Windows 7 systems are BIOS not UEFI, if actually UEFI post back. Then you have to use gpt on external drive and include an ESP on external drive.

---

### Post by mrpaskal on 2017-04-12
Thank you very much for your help !

---

