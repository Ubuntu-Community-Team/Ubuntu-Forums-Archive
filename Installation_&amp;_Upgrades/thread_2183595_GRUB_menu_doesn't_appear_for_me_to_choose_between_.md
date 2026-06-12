---
title: "GRUB menu doesn't appear for me to choose between Windows 8 and Ubuntu 3.10"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by lee589 on 2013-10-25
I ran the boot-repair, restarted my computer from the liveUSB when boot-repair was finished and my computer still automatically boots into windows.

Here is the URL boot-repair gave me:
paste.ubuntu.com/6301707

---

### Post by su:bhatta on 2013-10-25
From the pastebin, it seems you chose to install grub not in /dev/sda but in /dev/sda5, i.e. in the Ubuntu Partition itself:

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

Hence your computer boots directly to the Windows.

What you can do is
1) Use this page as guide and install Grub in /dev/sda
2) Use a Program like EasyBCD in WIndows and make a dual system boot with it.
These are the steps you have to follow:

Launch the program and select ADD NEW ENTRY from the EasyBCD Toolbox


Select the 'Linux/BSD' from the operating systems column 


Choose GRUB (Legacy) under type and Click on the ADD ENTRY icon 


Choose YES to the restart prompt 


GRUB will be displayed after the restart which will detect the Ubuntu partition for you to be able to boot into Ubuntu

---

### Post by oldfred on 2013-10-25
You have an UEFI system and it looks like an Ultrabook or system with small SSD used to cache Windows often using Intel SRT. The Intel SRT uses RAID which usually causes grub install issues as with RAID grub does not install "normally" but installs into the root of RAID. You would not want that anyway as it would interfere with the Intel SRT.

It does look like you have an ubuntu folder in your efi partition, so did grub install into it. With UEFI you have to go into UEFI and choose which system to boot. You do not show the signed kernels, so you must have secure boot off. With secure boot on, only signed secure boot systems will boot.

More info in link in my signature.

---

