---
title: "GRUB won't boot after dual OS install"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by chris336 on 2015-01-04
I just installed 14.10 along side Windows 7.  After restarting the computer GRUB never came up. I already tried the boot-repair and it said it worked but didn't.  Here is my info from that: [http://paste.ubuntu.com/9674838/](http://paste.ubuntu.com/9674838/).

I'm a new Ubuntu user and I really appreciate the help!

---

### Post by grahammechanical on 2015-01-05
Try this

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 7 in installed in EFI mode. That means that Ubuntu needed to be installed in EFI mode. That may have been the case. Anyway, Boot Repair has made sure that the correct EFI boot files for Ubuntu are in the correct partition. Boot Repair also gives this advice.

> Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda [COLOR=#666666]([/COLOR]3001GB[COLOR=#666666])[/COLOR] disk!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, [COLOR=#AA22FF]**then **[/COLOR][COLOR=#AA22FF]type [/COLOR]the following [COLOR=#AA22FF]command [/COLOR]in an admin [COLOR=#AA22FF]command [/COLOR]prompt:
bcdedit /set [COLOR=#666666]{[/COLOR]bootmgr[COLOR=#666666]}[/COLOR] path [COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\u**[/COLOR]buntu[COLOR=#BB6622]**\s**[/COLOR]himx64.efi

Please confirm that you have followed the advice.

Regards.

---

### Post by oldfred on 2015-01-05
What brand/model system?

You seem to have some issue with partitions.
       
 /dev/sda6   3,402,842,112 2,639,306,751[COLOR=#ff0000]  -763,535,360[/COLOR] Data partition (Linux)

You cannot have a minus partition size.

Download into live installer gdisk and post this:
sudo apt-get install gdisk
       sudo gdisk -l /dev/sda

---

### Post by chris336 on 2015-01-05
> **grahammechanical said:**
> Try this



[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 7 in installed in EFI mode. That means that Ubuntu needed to be installed in EFI mode. That may have been the case. Anyway, Boot Repair has made sure that the correct EFI boot files for Ubuntu are in the correct partition. Boot Repair also gives this advice.



Please confirm that you have followed the advice.

Regards.

Tried both with no luck,

> What brand/model system?

You seem to have some issue with partitions.
       
 /dev/sda6   3,402,842,112 2,639,306,751[COLOR=#ff0000]  -763,535,360[/COLOR] Data partition (Linux)

You cannot have a minus partition size.

Download into live installer gdisk and post this:
sudo apt-get install gdisk
       sudo gdisk -l /dev/sda

This system is a custom build:

CPU: i7 920
MOBO: x58-UD5
RAM: 6gb
HDD: 3 TB Seagate
GPU: 2 Radeon HD 5850s Crossfire

Here is the data from gdisk:

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6C198DA9-089D-4A11-A9FB-78CBE0CF464C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992      3164561407   1.5 TiB     0700  Basic data partition
   4      3164561408      3379404799   102.4 GiB   8300  
   5      3379404800      3402842111   11.2 GiB    8200  
   6      3402842112      5860532223   1.1 TiB     8300

---

### Post by alfred8 on 2015-01-06
Hi,

Have you tried commenting out GRUB_HIDDEN_TIMEOUT?

sudo gedit /etc/default/grub

Change GRUB_HIDDEN_TIMEOUT to #GRUB_HIDDEN_TIMEOUT.

then sudo update-grub and reboot your PC.

Regards!

---

### Post by chris336 on 2015-01-06
> **alfred8 said:**
> Hi,

Have you tried commenting out GRUB_HIDDEN_TIMEOUT?

sudo gedit /etc/default/grub

Change GRUB_HIDDEN_TIMEOUT to #GRUB_HIDDEN_TIMEOUT.

then sudo update-grub and reboot your PC.

Regards!

Attempted this but upon the sudo update-grub command I received the following message:

/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

---

### Post by oldfred on 2015-01-07
Sounds like you did the changes & updates to the live installer which will not work, not on your install.

Did gdisk say you had any errors? or loading backup, not primary? If so and partitions look ok, then do a w to write changes.
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by chris336 on 2015-01-07
I don't recall any error with gdisk.  Although, evertime I load up Ubuntu from Live CD I get the following error before the list of options: Unable to load: "fallback/boot.efi" on line 14.  That probably isn't the exact error but it's close.

---

### Post by oldfred on 2015-01-08
Some UEFI have a fall back setting. 
See post #11 for possible solution. Copies grub to fallback.efi.

       Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

---

### Post by chris336 on 2015-01-08
> **oldfred said:**
> Some UEFI have a fall back setting. 
See post #11 for possible solution. Copies grub to fallback.efi.

       Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

I tried to do it but wasn't able to find the file anywhere.  I even checked to see if they were hidden.  The post was very broad also.  Not sure exactly where to copy from or to.  This is getting frustrating.  I have been trying for about 3 days now.

---

### Post by oldfred on 2015-01-09
Some systems do not have a /EFI/Boot folder in the efi partition, but you do.

Then look at post #11 and copy grub or shim into it and rename it.
May be easier with Nautilus from live installer.

If using terminal:
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda1 /mnt
#only if not already existing, 
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
cp /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 
cp /mnt/EFI/Boot/shimx64.efi /mnt/EFI/Boot/fallback.efi

---

### Post by chris336 on 2015-01-14
I want to thank everyone who helped with this.  I did was oldfred said and it works perfectly!

---

### Post by oldfred on 2015-01-15
Glad you got it working. :)

Please change status to solved.

---

