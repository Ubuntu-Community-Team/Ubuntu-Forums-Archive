---
title: "Boot Problem After Installation New Laptop"
date: 2017-04-09
forum: Installation &amp; Upgrades
---

### Post by bettylu on 2017-04-09
First of all i am newbie to all this. I've just buy a new laptop Acer  Aspire E5-575-584A with only one ssd and its comes with an Acer Linux  distribution. I've install Lubuntu 16.04 Lts fine but when i installed  Ubuntu Gnome 16.04.02LTS something happen, finally i installed Ubuntu  14.04 Lts and the error is still the same. I am new to this and i  confused about the UEFI-Legacy  installation. I've try a lot of things  but nothing works. My laptop cannot boot from ssd, only from a  Liveusb/cd. But when i try for a new installation it seems that the ssd  has the Ubuntu 14.04. I've got this message when i open it and i cannot  find an answer on the web :

  
[LIST]
[*]Failed to open \EFI\Microsoft\Boot\mnx64.efi - Not Found 
[*]Failed to load image \EFI\Microsoft\Boot\mnx64.efi - Not Found 
[*]Failed to star MokManager : Not Found 
[*]Failed to open \EFI\Microsoft\Boot\grub64x.efi - Not Found 
[*]Failed to load image \EFI\Microsoft\Boot\grubx64.efi : Not Found 
[*]start_image() returned Not Found 
[/LIST]
  AND afters one-two seconds the message becomes:  
       
[LIST]
[*] Failed to open \EFI\Boot\max64.efi - Not Found 
[*] Failed to load image \EFI\Boot\max64.efi - Not Found 
[*] Failed to star MokManager : Not Found 
[*] Failed to open \EFI\Boot\grub64x.efi - Not Found 
[*] Failed to load image \EFI\Boot\grubx64.efi : Not Found 
[*] start_image() returned Not Found 
[/LIST]
 


  This is me Boot Repair Summary :  [URL="http://paste2.org/9yXK4yZW"]http://paste2.org/9yXK4yZW

[/URL]

  I will appreciate your help a lot, i bought this 2 days ago. Sorry for my bad english.

---

### Post by oldfred on 2017-04-09
It still shows some Windows UEFI boot files in ESP?

You have an Acer.
Acer has a unique UEFI requirement that you must set a supervisory password (never lose that or reset after configuration) and then from Within UEFI enable "trust" on the ubuntu/grub .efi boot files. 
I think only the Windows boot files have trust set automatically.

Also make sure you have newest UEFI version from Acer. Some older threads mention downgrading UEFI to get it working, but newer threads show newest UEFI from Acer works.
 Acer Trust Settings - details:
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

You also show 14.04.3 which is obsolete. Only original 14.04, 14.04.1 which were frozen with original kernel or the updated kernels in each point release until 14.04.5 are LTS supported until 2019.
      
 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

You also show flash drive as sda & internal drive as sdb. That may be causing you issues as Grub only wants to install to the ESP - efi system partition on drive seen as sda. If doing a new install, we may have to copy /EFI/ubuntu folder from flash drive installer to internal drive before rebooting after install.
Please add to this bug report if that is the case. It now says triaged, but still not solved in your case. Point out that your system makes internal drive sdb, where you want to install the boot loader and installer does not let you.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

---

