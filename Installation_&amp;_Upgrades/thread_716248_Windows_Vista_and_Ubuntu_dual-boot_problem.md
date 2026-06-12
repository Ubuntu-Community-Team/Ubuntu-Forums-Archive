---
title: "Windows Vista and Ubuntu dual-boot problem"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by 0vermind on 2008-03-05
It all started when I got tons of problems with Vista so I grabbed Ubuntu and installed.

Here is my problem:
I got grub all setup on the drive Ubuntu is installed on, I am pretty familiar with Grub and Ubuntu but not an expect (far from it).

I remember I had this same exact problem last time I wanted Ubuntu, I could not for the life of me get grub to add SUCCESSFULLY on the Vista Boot Loader.

I must have the Vista boot loader, I do not want or need the Grub Boot Loader I am more familiar with Vista and would like only 1 menu for multi-booting and os installs I do.

I have search and searched and searched through forums and on Google for the past few days, finding many solutions for other people but not of them worked for me.
Lets go through what I have tried:

Booting into Ubuntu through Super Grub Disk and grabbing the boot section and saving it to ubunut.bin it was something like "dd if=sda /dev/flashdrive/ubuntu" or something and it saved the 512 byte file but when I add that to the Vista boot loader the screen shows one word "GRUB" that's it. It does not boot to Ubuntu or anything.

I have tried VistaBootPro, bcdedit, and EasyBCD to create entries to boot Ubuntu and to boot sector bin files. In short I mostly used EasyBCD to add entries that linked to a NeoGrub.bin file that linked to a Menu.lst this works but it won't boot Ubuntu it shows "Invalid partition or non existent" (something along those lines). I have also tried plain setting it up and selecting the disk from EasyBCD, that doesn't work.

I have gotten one entry to work, however it DOES NOT boot to Ubuntu but instead boots to a Console line of Grub where I can do commands like find, root, boot, configfile, kernal, etc. However when I use this Command Line it says
"Warning: Unrecognized partition table for drive 81. Please rebuild it using a Microsoft- compatible Fdisk tool (err=24) current C/H/S= [didn't write down the numbers here]." and then it just sits there and does nothing. Other people have had this error but they say it boots fine though. It does not boot fine for me.

I have tried reinstalling grub to the disk that does nothing it just says "checking.... OK" and stuff but it did not reinstall grub.

I know this is not my hard drive, there are no bad sectors or anything. It has no problems and I have NTFS partitions on this drive too and no data has been lost. Further more I have reinstalled Ubuntu thinking that was the problem with no avail I am stuck with no way to boot Ubuntu with using Super Grub Disk.

I really do not want to use any other boot loader except BCD (Vista Boot Loader).

Please, please, please I really need help. I want off the Vista Express Train. 

Thanks so much for your time reading this novel/book of my problem!
-Mike

---

### Post by Rohan sehgal on 2008-03-06
dear sir,
can you please send me a copy of your vista boot file:). it will be an .mbr or .conf file.
this problem generally arises if your vista boot priority(not BIOS) is set to "grub-#overwrite-true#"

Anything more?
please contact me:-
[email]rohan.upclose@gmail.com[/email]
:lolflag::lolflag:

---

### Post by 0vermind on 2008-03-06
How do I convert my Vista to a .MBR?

---

### Post by 0vermind on 2008-03-10
Any help here? Please help me someone. I am able to partally boot Ubuntu by going into the bios and telling it to boot my second harddrive so that works but then I can't boot into windows. It's one or the other so that's not an option.


Please help me!!


Thanks in advance,
Mike

---

### Post by Computer Guru on 2008-03-10
How closely did you follow the official dual-booting instructions at [http://neosmart.net/wiki/display/EBCD/Ubuntu?](http://neosmart.net/wiki/display/EBCD/Ubuntu?)

---

### Post by 0vermind on 2008-03-12
Yes I did exactly that and it comes up saying
"Can not find partition" or 
"Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool  (err = 26). Current C/H/S=155217/255/63."

I think what is happening is because in Windows when I use EasyBCD or what ever, Windows marks the IDE HardDrive as 1 because it's logic is Vista is on 1 so it swaps the numbers so now Vista is on 0, but on the boot menu created by these programs for booting linux is adding( hd1,whatever)  but that's not right because it's changed after windows boots. So I don't know how to avoid this.

I'm not even sure if I'm explaining it right but there is my drive layout.

So I have a SATA and an IDE HardDrive:

IDE HardDrive (Usually this is marked as Primary Hard Drive but in Windows it's Secondary cause Vista is on the SATA)
  - Partition 1 = NTFS Partition for use in Windows (hd1, 1)
  - Partition 2 =  Linux Swap File System (hd1, 5)
  - Partition 3 = Ubuntu on EXT2 (hd1, 6)

SATA HardDrive (This is normally Secondary HD but since it's the bootable it's marked as Primary)
  - Partition 1 = Vista
  - Partition 2 = XP
  - Partition 3 = NTFS Partition for all of my junk I keep around (:P)

I have no idea how I did this before, it would be really helpful if someone could help me figure this out!


Thanks,
Mike

---

### Post by froy02 on 2008-03-12
Boot with the Live Cd and post the output of 'fdisk -l' and your menu.lst.

---

### Post by Computer Guru on 2008-03-13
> **0vermind said:**
> Yes I did exactly that and it comes up saying
"Can not find partition" or 
"Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool  (err = 26). Current C/H/S=155217/255/63."

I think what is happening is because in Windows when I use EasyBCD or what ever, Windows marks the IDE HardDrive as 1 because it's logic is Vista is on 1 so it swaps the numbers so now Vista is on 0, but on the boot menu created by these programs for booting linux is adding( hd1,whatever)  but that's not right because it's changed after windows boots. So I don't know how to avoid this.

I'm not even sure if I'm explaining it right but there is my drive layout.

So I have a SATA and an IDE HardDrive:

IDE HardDrive (Usually this is marked as Primary Hard Drive but in Windows it's Secondary cause Vista is on the SATA)
  - Partition 1 = NTFS Partition for use in Windows (hd1, 1)
  - Partition 2 =  Linux Swap File System (hd1, 5)
  - Partition 3 = Ubuntu on EXT2 (hd1, 6)

SATA HardDrive (This is normally Secondary HD but since it's the bootable it's marked as Primary)
  - Partition 1 = Vista
  - Partition 2 = XP
  - Partition 3 = NTFS Partition for all of my junk I keep around (:P)

I have no idea how I did this before, it would be really helpful if someone could help me figure this out!


Thanks,
Mike
You may have run into a bug in the NeoGrub routines, try replacing NeoGrub and NeoGrub.mbr (in C:\ and C:\NST\ respectively) with the files attached here:
[http://neosmart.net/forums/showpost.php?p=10974&postcount=22](http://neosmart.net/forums/showpost.php?p=10974&postcount=22)
(you may have to log in to be able to see attachments)

---

### Post by 0vermind on 2008-04-13
I outputted the commands you wanted (from Ubuntu, I had to change the BIOS settings to boot though)....

```

~$ sudo fdisk -l
sudo password for |UNDISCLOSED|:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 32 sectors/track, 30526 cylinders
Units = cylinders of 7680 * 512 = 3932160 bytes
Disk identifier: 0x000349fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30525   117215984    f  W95 Ext'd (LBA)
/dev/sda5               2       22525    86492160    7  HPFS/NTFS
/dev/sda6   *       22526       25192    10241264   82  Linux swap / Solaris
/dev/sda7           25193       30525    20478704   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdb2            8925       30514   173421675    f  W95 Ext'd (LBA)
/dev/sdb5            8925       12239    26626048    7  HPFS/NTFS
/dev/sdb6           12240       30514   146793906    7  HPFS/NTFS

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7872     2015216    e  W95 FAT16 (LBA)

```
-------------------------------------------------------
**Here is my explanation of each of these partitions:**

Okay so /dev/sda1 is the logic layer that enables me to have more than 4 partitions.
sda5 is a backup partition for my backup program in windows
sda6 is Ubuntu's swap partition
sda7 is Ubuntu

- sdb2 is suppose to be my Windows XP
- sdb5 should start on 30515 but for some reason it starts where XP starts.
    So something happened here. ***SDB5 is Windows Vista***
- sdb6 is a NTFS drive to keep all of my videos, photo's music, archives, and other stuff (like I said, Junk).

sdc1 is a 2GB USB ThumbDrive for Windows Vista ReadyBoost.

I don't think Vista and XP partitions are suppose to overlap like that are they? Is there anyway I can fix this without losing any data. I mean my data on the Vista drive is most important. The data on my XP drive if lost wouldn't be a big deal for me. 
(Not saying I want to lose it, it just isn't a big deal).


> **Computer Guru said:**
> You may have run into a bug in the NeoGrub routines, try replacing NeoGrub and NeoGrub.mbr (in C:\ and C:\NST\ respectively) with the files attached here:
[http://neosmart.net/forums/showpost.php?p=10974&postcount=22](http://neosmart.net/forums/showpost.php?p=10974&postcount=22)
(you may have to log in to be able to see attachments)
**Computer Guru:** In any case wouldn't I want to fix the partition mapping first before doing anything else to the bootloader?


Thanks for the help I've gotten so far!
-Mike

---

### Post by Lantesh on 2008-04-13
I am not trying to be a smartass here, but I am wondering why you simply just don't forget about the Vista bootloader, and use Grub.  Especially since the last operating system you installed was Ubuntu.  Your sources.list file will now have your Windows install listed on the Grub menu.  All you really need to do is use your live CD, or your Super Grub Disk and do a Grub repair, and when you reboot the Grub menu should come up with both OS's showing as options.  I know this is not the route you said you wanted to go, but honestly this is going to be your easiest fix.

---

### Post by 0vermind on 2008-04-14
> **Lantesh said:**
> I am not trying to be a smartass here, but I am wondering why you simply just don't forget about the Vista bootloader, and use Grub.  Especially since the last operating system you installed was Ubuntu.  Your sources.list file will now have your Windows install listed on the Grub menu.  All you really need to do is use your live CD, or your Super Grub Disk and do a Grub repair, and when you reboot the Grub menu should come up with both OS's showing as options.  I know this is not the route you said you wanted to go, but honestly this is going to be your easiest fix.
I just haven't been booting into Ubuntu for the last 4 weeks but with the increase problems and blue screens in Vista recently and the problems with their Service Pack 1. It has caused me to look back at these problems and see if I can fix these problems.

People might say "why not get rid of Vista". Well wine isn't perfect and Vmware isn't good enough so I have to boot into Vista. Some of my programs require Vista. The tech industry on the Windows side whether you like it or not is moving to Vista and away from XP. I mean just last week Microsoft made the official announcement that XP will be discontinued no matter how many petitions we make for it to stay.

Grub isn't what I need. It's too simple for my needs. Not only that but I have to boot through 2 menus if Vista gets rebooted (recovery menu) or if I need to boot other oses that won't work on Grub.

I just want the Vista Bootloader. I had already thought of using Grub. Besides that but I have had problems with it when upgrading Ubuntu the grub menu would go corrupt.


Thanks for the help though.

Any other ideas anyone?


-Mike

---

### Post by 0vermind on 2008-04-20
I refuse to believe that there is no solution to getting Ubuntu on to the Windows Vista Bootloader. It has to be possible. Please can someone help me??

Is the Linux community falling into the same hole that Windows is? I sure hope not. I love Linux. :cry:


-Mike

---

### Post by 0vermind on 2008-04-26
Here is the exact message I get when trying to boot Ubuntu on the Vista Boot Loader:

```

Booting 'find /nst/menu.lst'
Find --set-root --ignore-floppies /nst/menu.lst
(hd0,0)
Filesystem type is ntfs, Partition type 0x7
configfile /nst/menu.lst
Turn on gate A20... Success.

Warning: Unrecognized partition table for drive 81 please rebuilt it using
Microsoft-compatible FDISK tool (err=28 ) Current C/H/S 16383/240/63
Starting cmain()... find --set-root --ignore-floppies /boot/grub/menu.list

Warning: Unrecognized partition table for drive 81 please rebuilt it using
Microsoft-compatible FDISK tool (err=28 ) Current C/H/S 16383/240/63

_

```

And that underscore is a blinking white underscore line. It blinks slowly.
I've tried just letting it sit there and nothing happends. No HD activity or anything. All I can do is press Ctrl-Alt-Delete to reset the computer or press the Reset button.


-Mike

---

