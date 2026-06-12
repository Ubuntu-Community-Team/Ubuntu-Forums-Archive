---
title: "Window on Uefi, Ubuntu on Legacy"
date: 2017-05-10
forum: Installation &amp; Upgrades
---

### Post by nigro.orlando on 2017-05-10
Hi!
I just picked my computer from the store where I left it to make an upgrade. 

They followed my instructions to install Windows on a separate SSD while disconnecting the SSD with linux on. 
It all went well and from the bios I gave the first priority back to Ubuntu in order to boot in Ubuntu and restore the Grub. But after updating the Grub Windows doesn't show up on it. 
 
I found out, doing boot-repair, that the reason is probably that while Ubuntu has been installed on legacy Mood. The new Windows installation in on Uefi mode. 

Is it right that the easiest way to go here is to do a fresh install of Ubuntu but on Uefi mode?

---

### Post by Bucky Ball on 2017-05-10
> **nigro.orlando said:**
> Is it right that the easiest way to go here is to do a fresh install of Ubuntu but on Uefi mode?

Yes. ;)

---

### Post by oldfred on 2017-05-10
Just be sure to boot installer in UEFI mode.
And with two drives, use Something Else and only partition in advance.

You can unplug Windows drive and have full install on Ubuntu drive.
But with both drives plugged in it will probably see the Windows drive as sda. And grub in UEFI mode only installs its boot files to drive seen as sda.

There is no issue with Ubuntu having its boot files in a separate folder in the ESP on sda. But I like to have an ESP - efi system partition on sdb, even if only for future use. Difficult to add an ESP 300-500MB FAT32 partition to the beginning of a drive when it is full of data. 

       Good advice on UEFI and two drive installs
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration) 

More info on UEFI installs in link in my signature below. Just updated with above link.

---

### Post by nigro.orlando on 2017-05-18
@Oldfred
I did the installation and in the regard to the Uefi - Legacy issues everything went well. I did however tried to do as you suggested unplugging window and so on but Windows still got a sda partitioning. 

I'm also having a little problem: it happens sometimes that when I choose windows from the grub the BIOS automatically set the windows boot manager as first boot priority on the next start. And I therefore need to go back into the bios to put ubuntu first again in order to access it.

---

### Post by oldfred on 2017-05-18
Some Windows/UEFI to reset Windows to first.
Windows will do that with upgrades/updates just like a grub update/reinstall will set it to first.

Grub only boots working Windows, so make sure fast start up is off in Windows as that hibernation prevents Linux NTFS driver from seeing all NTFS partitions. And if chkdsk needed, you have to directly boot Windows from UEFI, not grub.
Best to also have Windows repair flash drive as well as Ubuntu live installer always available.

Some do one of the many work arounds.
One is to add Ubuntu to Windows BCD, you then always boot Windows, and Windows will let  you one time reboot into Ubuntu. 
Some add the fallback or hard drive boot entry which usually UEFI lets you keep as first entry.

What brand/model system.

Boot-Repair now copies shimx64.efi to be /EFI/Boot/bootx64.efi  as a fallback entry. Some UEFI will auto find that, others may require you to use efibootmgr to manually add an entry.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
See link in my signature for more info or:
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

---

