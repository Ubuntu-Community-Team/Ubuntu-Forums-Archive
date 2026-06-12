---
title: "Completely delete Ubuntu 14.04 LTS UEFI and restore Windows 8.1 bootloader"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by Ashwn on 2014-11-17
Hi.I have Ubuntu 14.04 LTS installed on my HP Laptop.
Here are the specs:

Intel Core i5 4210U
4GB DDR3 RAM
Nvidia Geforce 830M 2GB DDR3
Windows 8.1 64bit

I've followed the instructions provided by a tutorial at
 [http://forums.linuxmint.com/viewtopic.php?f=42&t=163126](http://forums.linuxmint.com/viewtopic.php?f=42&t=163126) to install ubuntu

The tutorial is for Linux Mint, but seemed similar to Ubuntu.

Ubuntu is up and running now on my notebook and I'm really happy with it.

Now my questions is how to completely remove Ubuntu from my laptop and restore the Windows 8.1 UEFI bootloader.
I'm not currently planning to uninstall Ubuntu but would like to know the procedure if I plan to uninstall in the future.

Ok so,What do I do to get Ubuntu completely out of the picture. I mean no dual boot screens(GRUB bootloader),no Ubuntu partitions - just plain Windows 8.1 booting under UEFI
Usually a HP logo with rotating circles animations appear if its normal.

This question might sound quite absurd for many Linux lovers here. But I need to know about this because my laptop's warranty would be screwed if any OS along with W8.1 is installed. RETURNING to Ubuntu after a long time so lots to keep up.This would'nt be a problem in a non-UEFI Based system.

Thanks.

---

### Post by flaymond on 2014-11-17
I'm a newbie, i can't tell you much because im still new. But what you would need (I believe) -

Copy of your Windows XP/7/8/8.1/10 to install the windows back into your PC.

I'll give you a link to check it out that suitable for your curiousity about the topic...

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by Ashwn on 2014-11-17
InterProg, I checked the link and this applies to PCs which would come with a installation disc.But my laptop does not come with an installation disc rather than a special 20GB bootable repair partition containing the whole W8.1 OS called as "RECOVERY DRIVE".

I don't know how I would be able to access that recovery drive to repair the MBR because the BIOS/UEFI menu can be accessed via Windows only.Normally F12 or DEL is usually pressed at boot to bring BIOS, but it not possible in my case.

---

### Post by yancek on 2014-11-17
I don't use windows 8 but, previous versions had an option to create a Recovery CD so that you could use it to reset to factory settings.  With that you would access your 20GB Recovery drive which would also overwrite Ubuntu.  If you did not create a Recovery CD when you initially booted windows, I'm sure there is some method to do it now.  Check some windows sites or the support.microsoft site.

---

### Post by Ashwn on 2014-11-17
yancek, what i'm trying to do is to remove ubuntu alone from dual boot and retain Windows ,not restoring it to factory settings. I have created a recovery CD as instructed by the OEM and tried to use it, but presented with an option to completely wipe out windows 8.1 and ubuntu. Now I dont want ..I just want to remove ubuntu and be as if its never been installed.

---

### Post by ubfan1 on 2014-11-17
Just use efibootmgr to change the boot order to put Windows first.  Then you will not see grub.  If you wanted to totally remove grub, there is no MBR to deal with in a UEFI machine, just remove the (EFI partition's) /EFI/ubuntu  directory and files.  On a removable media, you might need to remove or copy the Windows bootloader (bootmgfw.efi) over the /EFI/Boot/bootx64.efi (and check that file on your hard disk too, since a copy of grub might be sitting there to be invoked at odd times).

---

### Post by oldfred on 2014-11-17
+1 on ubfan's suggestion.

You have to first remove the ubuntu folder from the efi partition or else UEFI will keep adding ubuntu entry to UEFI NVRAM. And the UEFI NVRAM remembers its settings and has to be manually removed. Some systems let you modify those settings in the UEFI boot options, others only work using efibootmgr.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

But whether dual booting or not, you must have a Windows backup and a Windows repair flash drive. Hard drives fail even without any notice and users do make mistakes. 
      
 The vendor recovery DVDs are just an image of your drive as purchased, which you should make if you may sell system later and need it "like new". If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Ashwn on 2014-11-18
oldfred,Ok I have already backed up Windows and did everything needed(Disk image, recovery drive) even before installing Ubuntu.

So now I have to boot up with the liveUSB and then type the efibootmgr command and delete the partition as per your instruction.
I can understand all that, but what will happen after that? Will the whole OS including GRUB be removed or will I stare at blank screen?

Now do I have to re-enable Secure Boot and Fast Startup to bring back the Windows 8.1 recovery process?.

---

### Post by oldfred on 2014-11-18
You first remove the folder (and only the ubuntu folder) in the efi partition. Windows still uses the Windows folder. 
Did you use Boot-Repair a while ago? It may have renamed files & you have to undo that. If not then remove the grub/ubuntu efi entry in the UEFI with efibootmgr. If that entry does not exist then it should boot Windows or you need to go into UEFI to set Windows as first in boot order. 

You still have to delete Linux partitions, best to do that from gparted as gparted sees them correctly so you know you are working with correct partition. 

Then use Windows disk tools to either reuse space as data partition d: drive or resize you main c: drive. And if you want you can reset fast boot and secure boot.

---

### Post by Ashwn on 2014-11-19
Ok oldfred thanks for your advice on uninstalling Ubuntu and I shall follow it when I wanna remove Ubuntu

---

