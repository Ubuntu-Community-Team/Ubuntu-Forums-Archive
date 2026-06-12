---
title: "Dual Boot Win7 &amp; Ubuntu 12.10 - GRUB repair caused empty grub menu"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by beneml on 2013-05-04
I am fairly new to Linux/Ubuntu and am in need of some help.  I have dual booted Windows 7 and Ubuntu 12.10 on 2 separate hard drives.  After several attempts, I was only able to get it working by changing the BIOS hd boot option.  I then found some threads on repairing the boot process by using Boot-Repair.  This helped somewhat but only after using EasyBCD did I get 2 menu options for Windows 7 and Ubuntu.  But when I clicked on the Ubuntu option, it would only load up to the Grub prompt.  So then I ran Boot-Repair again after trying to do some partion work that Ubuntu stated I needed to do and it uninstalled Grub and reinstalled it (and I think I installed it onto the windows 7 hd).  Now when I boot up, it goes to the GRUB menu option but only shows System Setup as my only option.  When I click on it, it prompts me with and error stating that there is no fwsetup found.  I'm kinda lost from here now and just want to have Grub give me the options to boot into Windows 7 or Ubuntu 12.10.  I have created the boot info file in case anyone can make heads or tails out of what is going on.  

One thing I forgot to mention, which may be most of my headaches in this process, is that I have a 500GB hd for windows 7 and 60GB ssd for Ubuntu.  My laptop is a Lenovo T530 which does have the option for UEFI but Windows 7 image is currently not using it.  I've read that diabling UEFI in the bios is the best way to make dual boot work but it didn't seem to matter for what I was doing whether it's on or off.  

I'm not at all familiar with configuring Grub so I haven't done anything to get the OS options in there. 

boot-repair file: [http://paste.ubuntu.com/5632548/](http://paste.ubuntu.com/5632548/)

My objective is to keep Grub as my boot menu and have the ability to select Windows 7 and/or Ubuntu.  I do want the OS's  to be on separate HD's and primarily have Ubuntu on the ssd.  

Any help with this is most appreciated.  Thank you.

---

### Post by oldfred on 2013-05-04
A bios_grub partition cannot have a format. Your sdb2 shows FAT32.
       If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

I often suggest both a 250MB FAT32 efi partition for UEFI boot as first partition and a 1MB bios_grub unformatted partition for BIOS boot on gpt drives that do not have Windows. Windows only boots from gpt partitioned drives with UEFI. But you can boot Ubuntu in either UEFI or BIOS from gpt and if a separate drive the Ubuntu can be gpt and the Windows MBR(msdos) with both BIOS boot.

You need to create a bios_grub partition on sdb and reinstall grub to the protective MBR of sdb. That should get you booting Ubuntu.

But Boot-Repair was not able to mount your sda1 or sda2 partitions and sda2 with FAT16 is unusual. It may not be mounting it if Windows is hibernated or needs chkdsk. Do you have a Windows repairCD or flash drive as Boot-Repair will not fix internal Windows issues. It can install a Windows boot loader to sda if it sees or can mount the Windows install.

You want to end up with grub in sdb and BIOS booting from sdb. And Windows boot loader in sda, so if you ever have issues with sdb you can use BIOS or one time boot key to boot from sda. But until Windows is fixed, grub will not add Windows to grub boot menu.

---

