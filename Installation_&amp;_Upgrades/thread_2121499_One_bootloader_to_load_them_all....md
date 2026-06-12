---
title: "One bootloader to load them all..."
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by mrsean on 2013-03-02
hi, I'm playing around with a multi-loader setup for Windows 7, Windows 8, Ubuntu 12.04 and want to include a partition to share files between them all. I see FS-Drive will allow windows to see an ex3 partition so thats the sharing files sorted, but I do wish to overcome 2 problems...

1. My first attempt has resulted in 2 boot loaders, first the Ubuntu loader which redirects me to windows loader to choose between 7 and 8. I jus want one loader to give all the choices, recommendations?

2. In creating my partitions for Windows, I've run out of physical paritions for my file share drive. Any partition recomendations to allow for 2 windows physical partitions, a files drive, ubuntu parition with logical partitions for root and /home to allow for clean ubuntu upgrades, and also considering partitions needed for bootloader and swap partitions?

I know I'm crazy running two versions of windows, but as I'm doing compTIA A+ certification to get a job in tech support I want to be able to play with different OS's so I have good experience to end my unemployed time and find my dream job. Any help and advice greatly appreciated. I'm using gParted for partitioning, and I don't mind clearing the drive and setting up from fresh, it's good experience and I just built this new PC so I'm putting it through it's paces. HDD size is 500GB. Standard install for Windows 7/8 uses max 20GB. Thanks for any advice and recommendations you may have :^)

---

### Post by oldfred on 2013-03-02
Windows really wants primary partitions to boot from. And the new versions want the hidden 100MB boot partition, but will install to one NTFS partition with the boot flag. The 100MB partition was so you could encrypt the main install and possibly get to a repair console if main install is corrupted. So make a repairCD/Flash and install in one partition. Then have one larger extended partition for NTFS data partition and all your Linux partitions as logicals. Depending on how you have installed you may be able to move boot files to main Windows install, use fixparts to convert Windows to primary if not primary.  But all other partitions must be next to each other so they all can be in one extended partition.

Post this
sudo fdisk -lu

 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/
[/URL]

---

### Post by mrsean on 2013-03-02
Thanks oldfred, the explanation of the Windows bootloading setups is really useful. It'll take a couple of days to try a new setup, once I get something that works the way I want, I'll post the set-up to help others following in my footsteps. If anyone else has further input, I'm all ears as this is my first time doing this and getting a single bootloader for Windows 7, 8, and Ubuntu would be real nice.

---

### Post by Mark Phelps on 2013-03-02
> **mrsean said:**
> ... and getting a single bootloader for Windows 7, 8, and Ubuntu would be real nice.
Don't think that is possible ...

GRUB boots Linux OSs and hands off control to Windows when you select a Windows OS -- and then, the Windows boot loader does the rest.

A Windows product, EasyBCD, can be installed in Windows to boot Linux distros -- but even then, it installs GRUB4DOS (a GRUB version that can be installed to a Windows filesystem), so in that case, GRUB still ends up booting Linux distros.

Sorry, but as far as I know, there is no "one boot loader to rule them all" ... but I could be wrong.

---

### Post by darkod on 2013-03-02
If you take care to have the win7 and win8 boot files separate, you will get two separate entries in the grub2 menu and you can boot it all with only one menu. As oldfred mentioned, the thing is that windows combines boot files of more than one installation, and the boot files are put where the boot flag is.

So, after installing the first windows version, create the ntfs partition with the size you want for the second version, use Gparted from the ubuntu cd in live mode to turn off the boot flag on the first installation and to turn it on on the second partition you prepared. Only then start the second windows install. That way the boot files will end up on the partition with the boot flag, in other words on the partition where the OS is, and they will not get combined with the boot files of the first version.

Having two separate sets of boot files will be detected by grub2 and it will make separate entries in its menu. That way you can boot any windows version without going through the second, windows bootloader, screen. Just make sure you play the boot flag right before/during the second install. Move it manually, since the installer doesn't do that for you. You select the win8 destination partition, but the installer will put the boot files where the flag is without asking you anything. You need to move the flag by hand in advance.

---

### Post by drdos2006 on 2013-03-02
> 
Sorry, but as far as I know, there is no "one boot loader to rule them all" ... but I could be wrong. 


This looks interesting.

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

regards

---

### Post by Mark Phelps on 2013-03-02
> **drdos2006 said:**
> This looks interesting.

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

regards

Right ... but that's to have on a portable USB device.  I didn't see anything there about having it on your desktop PC.

---

### Post by darkod on 2013-03-02
> **Mark Phelps said:**
> Right ... but that's to have on a portable USB device.  I didn't see anything there about having it on your desktop PC.

As mentioned above, this is very easily doable if you take care windows not to combine the boot files. With two sets of boot files grub2 will make two entries, just what you need to boot everything directly from grub2 menu. Two windows plus ubuntu.

---

