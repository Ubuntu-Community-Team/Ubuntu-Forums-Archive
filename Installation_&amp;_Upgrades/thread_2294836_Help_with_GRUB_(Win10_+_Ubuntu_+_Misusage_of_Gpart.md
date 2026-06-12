---
title: "Help with GRUB (Win10 + Ubuntu + Misusage of Gparted)"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by pedro_henrique3 on 2015-09-13
Hi,

All the time that I try to install an Ubuntu version I make some mistakes during the installation...

My laptop was running Windows 10 and after hear some about the security issues of the new version, I wanted to go to back to use linux...

So I installed the Ubuntu - Gnome version, and I was not able to boot after installing the Ubuntu using GRUB. I was only able to boot in Windows... Then I made the total mistake with GParted... :guitar:

I excluded the SDA1, then everything stop working... Then I installed the boot-repair and now I`m using the live usb...

The mensage of error is the following...

[http://paste.ubuntu.com/12401693/](http://paste.ubuntu.com/12401693/)

Could please someone help me, I do not want to format all the data in the hard drive and start again... 

Thanks!!!

Pedro Henrique

---

### Post by oldfred on 2015-09-13
It looks like your system was UEFI and then you have to have an ESP - efi system partition. That is a FAT32 formatted partition with the boot flag if using gparted. That is then where UEFI looks for efi boot files.

And with gpt no other partition should have boot flag. But you have three partitions with boot flag.

If Windows was originally BIOS then you converted drive to gpt. 
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.

Ubuntu will boot in BIOS mode from a gpt partitioned drive, but needs a 1 or 2MB unformatted partition with the bios_grub flag. Or with UEFI you need the ESP. You are not showing either, so grub cannot correctly install.

I would convert sda1 to FAT32 and make sure it and only it have boot flag. Then boot Boot-Repair in UEFI mode and reinstall grub-efi-amd64 for UEFI boot.

You should also have a small Windows partition just before the NTFS partition.
       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Boot-Repair cannot fix major Windows issues. Your really need a Windows repair flash drive or installer and reinstall its boot files in UEFI mode.
       
 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)
Or if you have a friend or other access to another system:
       
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by pedro_henrique3 on 2015-09-13
First of all, thanks for the answer and help... 

Since I'm not so familiar with this new UEFI... I was used with obly MRB and normally I make some mistakes... 

What I understood is:
1 -  create a small partition without any format with a size of 1-2mb. And put the flagship boot-grub
2 - change the sda1 to fat32 and only this hd with boot flag
3 - remove the boot flag from sda2 and sda 3

With this I'll be able to boot Ubuntu? 

Regards, 

Pedro Henrique

---

### Post by oldfred on 2015-09-13
You do not need both a bios_grub partition and an ESP. Although I do have both just in case.

You need the bios_grub for BIOS boot and then you boot Boot-Repair in BIOS/CSM/Legacy mode and install grub-pc. 
Or you need the ESP for UEFI boot. And can boot Boot-Repair in UEFI mode and install grub-efi-amd-64 for UEFI boot.

If you install grub for BIOS boot you will not be able to boot Windows from grub menu, only from UEFI menu as UEFI & BIOS are not compatible. Grub only boots Windows installed in same boot mode. And you cannot convert Windows to BIOS boot if drive is gpt partitioned, without a totally new install.
Was Windows originally UEFI?

---

### Post by pedro_henrique3 on 2015-09-13
I believe that the Windows was a UEFI installation. Because I did it by the standard procedures... I try to read the link at your signature and see if I can find some more answers...

Thanks again...

---

