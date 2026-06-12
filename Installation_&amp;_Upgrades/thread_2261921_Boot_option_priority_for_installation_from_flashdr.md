---
title: "Boot option priority for installation from flashdrive."
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2015-01-21
I have Ubuntu 12.04 in  my desktop and trying to install lubuntu in a new laptop by creating a bootable pendrive containing lubuntu 64bit (created using unetbootin which is there in my old desktop). The laptop contains free DOS already so I need to keep it as it is and install  lubuntu to give me a dual boot set up. The problem is the three boot option priorities are: 1. Uefi ip4 realtek PCIe FE family controller, 2. Same as above with ip6, 3. Harddisk. I do not understand meaning of uefi and confused whether for my purpose of installing from bootable pendrive I should keep this default order unchanged or should I make harddrive as first option. If all three are unsuitable should I add a new boot option like USB and make it first option? This type of addition of boot option is allowed. This is my first question. 

My second doubt is: while using the pendrive in my desktop a folder lost+found was created automatically and this is still there in pendrive along with all the other installation specific files created by unetbootin from lubuntu iso. Many people in Ubuntu forum advise against removal of lost+found folder. Should I keep this folder in the pendrive and proceed for installing lubuntu in laptop? Will that be harmful?

---

### Post by Ko_Char on 2015-01-22
> **arroy_0209 said:**
> The problem is the three boot option priorities are: 1. Uefi ip4 realtek PCIe FE family controller, 2. Same as above with ip6, 3. Harddisk. I do not understand meaning of uefi and confused whether for my purpose of installing from bootable pendrive I should keep this default order unchanged or should I make harddrive as first option. If all three are unsuitable should I add a new boot option like USB and make it first option? This type of addition of boot option is allowed. This is my first question. 

1, 2 - are for network. They are skipped if not present.  
UEFI is a replacement for BIOS. It is present in recent computers (with Windows 8, 8.1). You have to use 64-bit version to install in UEFI mode. You can read more about UEFI [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
You can see whether you are in UEFI mode or not in the above article. Look at the picture.

If the USB is properly created, there should be another boot entry for USB Stick. In my laptop, I can use F12 - to boot from USB Stick. It starts with UEFI - like UEFI Kingston USB Installer (Keys varies depending on laptop models)

May be others can help with partitioning and proper method of installation. Also mention your laptop model. It might help.

---

### Post by arroy_0209 on 2015-01-22
Thanks for your reply. Here is my Asus laptop model no. - X200LA-KX034D. Processor is Intel core i3 4010U and RAM is of 4gb. If anyone has experience with this type of laptop, I will appreciate any further suggestions. Thanks.

If I understand  correctly I need to add boot option USB since harddisk is not appropriate here. Is that correct?

---

### Post by oldfred on 2015-01-22
A lot of new computers only boot the Windows option by description in UEFI menu, not the ubuntu entry that will be created. Several work arounds are to rename the ubuntu entry to be "Windows" in UEFI. Or to copy grub/shim boot files into a /EFI/Boot/bootx64.efi file that is the hard drive boot entry.

If system came without Windows it really should not have the UEFI description restriction.

       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

Usually UEFI settings are similar by Brand as the use the same UEFI and only the options are different. So some of these may be similar.

 Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)
       
 UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

