---
title: "Windows 8.1 64-bit dual boot Toshiba SATELLITE C55-A-1NN, boots directly to Windows"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by giotoula on 2014-12-12
Hello all.

I am creating this thread to transfer a problem I posted elsewhere in the forum, and ask some further questions.
I installed Ubuntu 14.04 on a Toshiba SATELLITE C55-A-1NN to make a dual boot system, but it bypasses the GRUB2 and loads directly Windows 8.1.  

You may want to know that on windows if I hit restart with the Shift key pressed continuously I enter a special UEFI screen where I can select a "Use a device" option. I can choose Ubuntu and load normally the GRUB2 and the Ubuntu. But this is quite impractical and I want to make the system work properly.

This is the Boot Info summary I got after unsuccesfully running boot repair [http://paste2.org/E3HcVyk4](http://paste2.org/E3HcVyk4).



So I am about to try the following steps (suggested at this post [http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)).

>                                                          Since you do not have any Windows you can just create the Windows  efi  boot file with the Windows name. Then the UEFI will think it is  booting  Windows but really boots grub.

You will have to recreate in the efi partition the Windows folder, a   boot folder under Windows and copy grubx64.efi into that folder and   rename it to bootmgfw.efi.

       mount /dev/sda1 /mnt
cd /mnt/EFI
      
   use ls to see if mounted correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi 

Most systems also have a /Boot folder and can boot grub from that using a hard drive entry.
mkdir Boot

cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

Your ls -l should then have this in the efi partition:

 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu                      

     
 



But I have three questions before I make  anything I regret.
1. I am confused with a 1GB partition I find at the start of my disk (  /dev/sda1, file system: ntfs, flags: hidden,diag) and the /dev/sda2,  fat32, 100MB partition flagged as boot. As I see at my Boot Info script  as well, [http://paste2.org/E3HcVyk4](http://paste2.org/E3HcVyk4), I think the /EFI directories are on sda2. So I want to make clear if I should mount /dev/sda1 or /dev/sda2.

2. At the Boot Info script again, I see there exists a bootmgfw.efi file  in a Microsoft/Boot directory. I am supposing that creating a Microsoft directory refers to a different problem.
Should I just replace the bootmgfw.efi  file with grubx64.efi (which I have to rename to bootmgfw.efi) or should  I follow the steps referred at the first link and make a Microsoft/Boot  directory?

3. It is suggested some times to backup the efi partition. Is it that  necessary? Because I cannot find any information I can understand. Can I use the cp -r command and copy the directory (which exactly?) in the /EFI partition with a different name or this would cause problems?


I hope asking for instructions as exact as possible (as I am not very familliar with all the linux story) is not too much a trouble.

---

### Post by oldfred on 2014-12-12
Before making any changes backup is vital. Some have totally erased  system by reinstalling as when Ubuntu says overwrite drive that is  entire hard disk, not the Windows definition of drive which may be just a  partition.
And if you may ever sell system and want a clean version,  you should make the vendor recovery DVD set. They do not provide that  with purchase any more, but you have to make your own. And if hard drive  fails it or a full backup are the only way to recover system.

       The vendor recovery DVDs are just an image of your drive as purchased.  If you have housecleaned a lot of cruft normally included, run many  updates with many reboots, and added software you may want a full back  up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Also  Linux tools cannot fix most Windows errors, so best to always have a  separate Windows repair tool. I always have several different tools for  the current version every operating system I have installed. For Ubuntu  the live installer is always good to have, but I usually download some  others also.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

The  efi partition is easy to backup, it is not large and does not require  any special commands to restore. You can just use any copy tool to copy  to another drive, flash drive or however you prefer to backup. And backup to another folder on the same drive is not really backup, but better than nothing. Hard drives do eventually failure and power surges, lightning, user error and many other issues can require you to have good backups.

Your efi partition is sda2.

I only suggest using the Windows filename to boot for those who have only Ubuntu installed. If dual booting creating or using /efi/Boot/bootx64.efi is much better. 
Boot-Repair used to rename the Windows file as that was the only way we knew. But then Windows updates would overwrite it, or issues getting into grub prevented any boot of Windows. If bootx64.efi is renamed you can still boot into Windows from UEFI boot menu or one time boot key often f12.

You already have the folder for /efi/Boot/bootx64.efi.
I would backup the bootx64.efi and rename it.

If with one time boot key or some work arounds you can get into Ubuntu the the efi partition is already mounted.
 This copies grubx64.efi over bootx64.efi.
sudo cp /boot/efi/EFI/grub/grubx64.efi /boot/efi/EFI/boot/bootx64.efi

If from live installer (not sure if sudo required or not with live installer, if permission error add sudo)

 From live installer mount the efi partition on hard drive, your /EFI/Boot already exists:
mount /dev/sda2 /mnt
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
cp /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.bkp
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

---

### Post by giotoula on 2014-12-14
Thanks a million oldfred.
Now I can just go back to studying physics again instead of computer science.
I did it via live installer usb and it works. Now I am just crossing fingers it stays that way. Except if the same steps apply in such a case (e.g. a major Windows update).

---

### Post by oldfred on 2014-12-14
Glad that worked.

If you do get a major grub update, you will need to copy grubx64.efi again as you may have grub version issues. I would keep a live installer handy to be able to do that. But minor updates or kernel updates should not create issues.

---

