---
title: "Drive partition scheme needed for multi boot system"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by KLund1 on 2015-07-17
I have a multi boot windows system over 2 SSD's and 2 additional data HDD's. I have attached a snip of my drive configurations from windows.  The SSD's are Disk 2 & 3. Disk 3 has a 47GB empty partition I want to install Ubuntu on. I know just enough about Linux to really mess me up, so I'm asking for advice before the install. 
I have read several Ubuntu install guides. I know that I will need to make a boot, swap, and root partitions. My rig has 16GB of ram. 
First I know Linux uses a very different drive naming system then windows. something like /dev/hd1. From the picture I have attached, can you show me what the designations of the new partitions I will have to make during the install, and what sizes for each that will fill the 47GB? I do have a current complete backup of both SSD's, and i will be using easyBCD to go back to the windows bootloader running first on boot. 
Many thanks

---

### Post by oldfred on 2015-07-18
It may be sdc, but best to boot Ubuntu live installer and go to terminal and post this:
sudo parted -l
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)

Most new Desktop systems do not need separate /boot and it can add complications. One more partition to manage size on.
And with 47GB may be best just to have / (root) and swap. And with that much RAM you probably never will use swap but put 2GB in anyway just to have some. Auto install may make swap too large.

You do want to install grub to same drive as Ubuntu install. Leave Windows boot loaders on the Windows drives.
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Grub will not boot Windows that is hibernated and Windows 8 or later is always hibernated as fast startup as that is the only way they make users think it boots as fast as Ubuntu(without hibernation). :)
If directly booting Windows using BIOS or one time boot key you may not have to turn fast startup off.
Best not to use EasyBCD, but a few have. It uses the very old grub4dos as boot manager to chain load to grub in another location. It may say to install grub to a partition and that is not recommended by grub. But with several MBR, installing grub to MBR on Ubuntu drive then can be chainloaded from another grub like grub4dos.


[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

