---
title: "Ubuntu 9.10 cannot boot from USB Hdd"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by SilviuM on 2009-11-23
Hello,

I have an Amilo Pa1510 laptop which has a broken SATA chipset and does not recognize anymore the internal HDD. Anyway I have bought a external usb rack for the hdd and decided to install Ubuntu on it.

The laptop is able to boot from USB devices as it can boot Ubuntu Live from the USb hdd.

I have tried to install Ubuntu on this usb hdd and did not manage to make it boot. 

When trying to boot the GRUB2 bootloader says only GRUB in the top left corner and nothing else (seems like it is not able to start the OS).

Can anyone give me some pointers on how to successfully install Ubuntu on my extern USB Hdd (a real installation not live one).

P.S. I have tried all the tutorials with no results. The only success I had was to install on the USB Hdd the Live Version and it starts up correctly, but I would like to have a proper install as I need to use the whole Hdd not just 4 Gb of it.

Thank you,

Silviu

---

### Post by raymondh on 2009-11-24
> **SilviuM said:**
> Hello,

I have an Amilo Pa1510 laptop which has a broken SATA chipset and does not recognize anymore the internal HDD. Anyway I have bought a external usb rack for the hdd and decided to install Ubuntu on it.

The laptop is able to boot from USB devices as it can boot Ubuntu Live from the USb hdd.

I have tried to install Ubuntu on this usb hdd and did not manage to make it boot. 

When trying to boot the GRUB2 bootloader says only GRUB in the top left corner and nothing else (seems like it is not able to start the OS).

Can anyone give me some pointers on how to successfully install Ubuntu on my extern USB Hdd (a real installation not live one).

P.S. I have tried all the tutorials with no results. The only success I had was to install on the USB Hdd the Live Version and it starts up correctly, but I would like to have a proper install as I need to use the whole Hdd not just 4 Gb of it.

Thank you,

Silviu


Try :

-  Do the usual install unto the external Hdd.
-  In step 7 of the install process, select "ADVANCED" and install GRUB2 unto the MBR of the external Hdd (and not the internal hd)
-  After the install, access your BIOS and make sure that the external Hdd is the FIRST TO BOOT and 'save as default' (since you say you don't need the internal hd anyways).

One reason why you get the GRUB prompt is probably you are installing GRUB2 to the MBR of the internal Hd (which is default, if not altered in step 7) and since you have problems with your system recognizing the internal ....

See what this does.  Post back any errors.

Happy ubuntu-ing.

---

### Post by SilviuM on 2009-11-25
Hi and thank you for your reply.

The laptop has no internal HDD (I have removed it and inserted it in the USB rack).

I have also entered into the advanced section of the install and set the bottloader to install on the first /dev/sda partition of the USB HDD (also tried just leaving (hd0) on this option I got Operating system not found).

The USB HDD is the only boot device as the laptop has no internal HDD nor Boot CD/DVD in the DVD/ROM unit. 

Thank you.

---

### Post by wikke on 2009-11-25
Hello,
 
 
*General info:*
I have a fujitsu siemens amilo pi2530 and I have encountered the exact same problem as the original poster.
 
I have disconnected my internal sata hard drive completely.
 
The BIOS recognizes my external USB drive and the boot order is set to booting that drive first.
 
Ubuntu is correctly installed. I tried various settings: letting Ubuntu manage partitions to choosing partitions myself. When choosing partitions myself, Grub was set to write to the MBR of the external drive. 
 
Similarly, I also tried installing Linux Mint 7 Gloria KDE, which gave the exact same problems as with the Ubuntu installations (not surprisingly).
 
*Problem info:*
**A fresh Ubuntu install** brings me to a screen with " **GRUB _** " (blinking underscore) on it. Nothing loads.
 
I have tried reinstalling grub from the LiveCD (which is explained here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) , chapter "Reinstalling GRUB 2").
After this is done, the computer gives the error " **Operating System Not Found** ".
 
Maybe this is an issue specific to the amilo line?
Any help is greatly appreciated.
 
Thanks, 
wikke

---

