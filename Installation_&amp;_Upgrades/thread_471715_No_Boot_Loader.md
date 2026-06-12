---
title: "No Boot Loader?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by RickJensen on 2007-06-12
[FONT="Garamond"]Hello -
I have downloaded the latest Ubuntu (7.04) release and booted to the CD, and ran the installer on the desktop. Everything completes with no error that I can see, but when I boot my computer without the CD it goes straight into Windows.  Is there an installation step I missed to install GRUB or LILO?  Or did I do the installation wrong altogether? I've never used Ubuntu before, only Fedora and its been a couple years since that.  Thank you in advance!

--Rick[/FONT]

---

### Post by Herman on 2007-06-12
Hello RickJensen,
A few computers have features built into their BIOSes that are supposed to prevent boot sector viruses from attacking the MBR.  To achieve this they either block anything from writing to the boot loader's area of the MBR somehow, or keep restoring the MBR from a backup copy of Windows IPL somehow it seems.  That's great if you only want to boot Windows for the life of the machine, but if you are trying to write to the MBR deliberately, like to install the IPL for Grub, it's a just a nuisance. See if you can go into your BIOS (CMOS) [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm")  and if there's some kind of  'MBR protect' feature of some kind and disable it for now, [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect").

If your computer has more than one hard disk, it is quite possible that Grub is getting mixed up about which is your first hard disk. This is likely if one is an IDE and the other is SCSI or Sata, or if you have your IDE hard drives plugged in and jumpered in an unusual way. ie: If you have 'cable select cables, the jumpers should be set to 'cs', if they're non 'cable-select' cables, then one should be jumpered as master and the other should be jumpered as slave. 
And then sometimes people, (or someone you had fixing your computer for you), switch things around in their BIOS in different ways too. That's another thing to look at, [    Make sure your hard disk is properly detected in your BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Making_sure_your_hard_disk_is_properly"). |   [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").    |    [Changing the boot sequence in CMOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS").    That can really be confusing for Grub too if your BIOS has settings like that and they have been set up in an unusual way. 

And finally, to get you booting for now, in case you don't already know, the most useful thing you can get is a copy of [Super Grub Disk]("http://geocities.com/supergrubdisk/"), that should help you boot for now and it is also the easiest and fastest way to install Grub to any MBR you like.

Good luck, 
Regards, Herman :D

---

### Post by RickJensen on 2007-06-13
Ok, now I have used the Super Grub Disk to reinstall GRUB to the MBR, I used the Automatic option.  Now when I boot I get the GRUB screen with 3 different Ubuntu options and my Windows installation, but when I choose any of them I get "Error 21: Selected disk does not exist."  Anyone seen this before, and know how it is fixed?  Now the only way I can boot either OS is through the Super Grub Disk.

---

### Post by Herman on 2007-06-13
[     Grub error 21]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21"). is normally quite an easy one to fix, likely you just have a small mistake in your /boot/grub/menu.lst file which can easily be corrected by editing that file.

First you need to find out the right information, about which hard disk your Ubuntu installation is on. You can do that by looking at it with GParted or any Linux partitioner.  
Fdisk is a good one that works from the command line, (from your terminal), for example 'sudo fdisk -lu' will give you the information you need.
```
 sudo fdisk -lu
```
For example you do 'sudo fdisk -lu and you find out your Ubuntu partition is /dev/hdb2. (second hard disk, partition 2),  
Now you will need to know what that is equivalent to in Grub's numbering system,  Here is a link, [A Quick Guide to Grub's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
[FONT=Tahoma]So for our example, [FONT=Bitstream Vera Sans Mono]/dev/hdb2 in Linux = [/FONT][FONT=Bitstream Vera Sans Mono](hd1,1)[/FONT][/FONT][FONT=Bitstream Vera Sans Mono][FONT=Tahoma] for Grub.

Then you open your /boot/grub/menu.lst, [/FONT][/FONT]
```
sudo gedit /boot/grub/menu.lst
``` ..and you look for your operating system entry for booting Ubuntu, which will be down somewhere  in the lower half of the file.
 Maybe it looks something like this, 
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd[COLOR=Red]**0**[/COLOR],2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` As you can see, the hard disk number listed here for telling Grub which hard disk to look on is wrong, it says '(hd0,2)' for first hard disk, partition 2. You know it's really supposed to be second hard disk, partition 2.

So you might fix the error by editing your menu.lst file with the correct hard disk number like this,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` Now you should be able to reboot and your hard disk installed Grub should work properly. :D

That has been an example of how to fix grub error 21 in a fictitious situation, your exact situation will probably be a little different, depending on your exact hard disk and partition arrangements.

If you have any more trouble, please post a copy from the bottom portion of your /boot/grub/menu.lst file here along with the output from 'sudo fdisk -lu' or a screencap from GParted.

Regards, Herman :D

---

