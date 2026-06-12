---
title: "installing ubuntu 14.04 on pre-installed windows 8 machine -- uefi or not?"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by kimberly2 on 2015-07-01
hi guys, so i got a machine that has windows 8 pre-installed and i want to dual boot ubuntu with it.

so i was following this link: [http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS) and doing alright. i used diskmgmt.msc from the command line to resize my C drive to ~480gb out of a total of ~980gb, and it appeared to work because not it appears as "unallocated".

i created a liveusb on my other ubuntu machine, using startup disk creator, and using a 14.04 .iso. that seems to have gone fine as well.

when i boot up the new machine with the usb in, and hit esc to select the boot device, my usb shows up in two sections: first, under a section "UEFI boot devices" and then i think another called "legacy devices", that include the cd drive and hard drive.

if i select the uefi one, it goes to the ubuntu menu with choices "try ubuntu without installing", "install ubuntu", etc.

at that point i go to install ubuntu and do the standard stuff, until i get to the part about overwriting the disk vs doing "something else" as they call it. because i want to keep windows, i select something else, and it brings me to gparted or something displaying my partitions.

here's where it got weird. what was clearly my big C drive that i split is still there as one ~980gb partition. so i did a bit of reading and asking and people suggested that it means that i have to do a uefi install. so i was following this guide: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

and it said to run as administrator (in w8) the command "Confirm-SecureBootUEFI". this gave me: 

**Cmdlet not supported on this platform** - Means your  system does not support Secure boot and most likely you do not need this  guide. You can install Ubuntu by simply inserting the LiveCD or LiveUSB  and doing the installation procedure without any problems.

hm. but now i booted up my liveusb, and doing sudo fdisk -l gives me:

warning: gpt detected on /dev/sda! the util fdisk doesn't support gpt. use gnu parted.

now, if i do sudo gparted, it gives me a pretty long warning:

/dev/sda contains gpt signatures, indicating that it has a gpt table however, it does not have a valid fake msdos partition table, as it should. perhaps it was corrputpd -- possibly by a porgram that doesn't understand gpt partition tables. or perhaps you deleted the gpt table, and are now using an msdos partition table. is this a gpt partition table?

and asks me to select yes/no.

at this point i'm pretty lost. first question: based on this, do i in fact have uefi or not? one thing suggests no, the other suggests yes.

my second question is, how do i proceed?

thanks!!

---

### Post by dino99 on 2015-07-01
'oldfred' posts/threads are the most usefull to explain the different cases (look inside that subforum)

---

### Post by Bucky Ball on 2015-07-01
Switch secure boot off in the BIOS. Make sure you have enough free space to install Ubuntu to. Shrink Windows partitions with Windows software. 

If you have one giant Windows partition, where are you going to install Ubuntu??? You need to shrink the win drive, switch secure boot off, boot the Ubuntu install media in EFI and install in EFI if you want to keep Windows.

Installing Ubuntu in legacy mode, which looks like what you are trying to do, when Win is installed in EFI is not going to work. They need to be the same, either EFI or legacy, not one of each.

---

### Post by kimberly2 on 2015-07-01
hi bucky ball, thank you for the reply.

however i thought the windows command i did (Confirm-SecureBootUEFI) was checking if my system supports secureboot, and by getting the result "**Cmdlet not supported on this platform"** it told me that it doesn't.

also, sorry if i wasn't clear, but what i meant before is that i already shrank the windows drive. now there's ~400something GB for ubuntu. so in windows my disk management looked just like this (taken from that guide): [http://cdn.instructables.com/FPR/4RIC/H337KGF2/FPR4RICH337KGF2.LARGE.jpg](http://cdn.instructables.com/FPR/4RIC/H337KGF2/FPR4RICH337KGF2.LARGE.jpg) except my numbers are different obviously.

the strange thing is that when i went to install it using the liveusb it didn't show the separate partitions (ie, the windows one and the one i just created using diskmgmt in windows), it just showed one big block. i actually just noticed that in the picture right above, he appears to have right clicked on the newly created unallocated space and there's an option "new simple volume" highlighted, but it doesn't say anything about that in the directions. was i supposed to do that too?

with regards to installing ubuntu in legacy mode, i'm not trying to do that specifically. i just want ubuntu installed on this computer and i don't care if it's uefi or legacy, i just want the easiest route.

the problem is that i'm getting conflicting info on whether w8 is even installed in efi: secureboot isn't supported, so i thought that meant no uefi, but fdisk talks about GPT, so i thought that does mean uefi.

what should i do?


edit: also one other question. in this askubuntu thread: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

he says: 
> If you are using Ubuntu 15.04+, many issues are now solved, so there  is no need to follow this guide except if you are using any Ubuntu  version older than 15.04. Depending on the version you are using (12.04,  14.04, 14.10) you might need all or some of the steps provided in this  answer.

  If however, you are using 15.04+, rejoice!, in all tests I have done  with 15.04+ there was no need to do any of the steps mentioned here, so  enjoy Ubuntu in all of it's booting glory!.


should i just get 15.04 instead? is it stable? i don't really care about the ubuntu version either as long as it works and is stable. would doing it with 15.04 solve this problem?

---

### Post by kimberly2 on 2015-07-01
okay i've figured out a little more but still confused.

i almost certainly have windows installed with uefi.

the windows partitions look the same (that is, with the new unallocated space) even after reboot when i use diskmgmt.msc, but from within ubuntu, the installer doesn't seem to.

running sudo fdisk -l gives me:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5f2763f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2115583     1056768    7  HPFS/NTFS/exFAT
/dev/sda2         2115584   963610623   480747520    7  HPFS/NTFS/exFAT
/dev/sda3      1922801664  1953521663    15360000   27  Hidden NTFS WinRE

Disk /dev/sdb: 7803 MB, 7803174912 bytes
241 heads, 62 sectors/track, 1019 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070c7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15225897     7612918    c  W95 FAT32 (LBA)
```

so it actually DOES appear to be recognizing one of the partitions (i guess the shrunk windows one?).

however sudo parted -l gives me a warning about it might having a GPT table, and asks me if it is. if i say no, nothing interesting happens, but if i say yes:

```
ubuntu@ubuntu:~$ sudo parted -l
 Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
 However, it does not have a valid fake msdos partition table, as it should.
 Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
 partition tables.  Or perhaps you deleted the GPT table, and are now using an
 msdos partition table.  Is this a GPT partition table?
 Yes/No? y                                                                 
 Model: ATA WDC WD10EZEX-60M (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/4096B
 Partition Table: gpt
  
 Number  Start   End     Size    File system  Name                          Flags
  1      1049kB  1074MB  1073MB  ntfs         Basic data partition          hidden, diag
  2      1074MB  1451MB  377MB   fat32        EFI system partition          boot
  3      1451MB  1585MB  134MB                Microsoft reserved partition  msftres
  4      1585MB  983GB   982GB                Basic data partition          msftdata
  5      983GB   1000GB  16.8GB  ntfs         Basic data partition          hidden, msftdata
  
  
 Model: Kingston DataTraveler 2.0 (scsi)
 Disk /dev/sdb: 7803MB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
  
 Number  Start   End     Size    Type     File system  Flags
  1      31.7kB  7796MB  7796MB  primary  fat32        boot, lba
```

so it appears to NOT be seeing it there.

another place it explicitly DOES see the unallocated space is if i use the "Disks" utility:

[IMG]i.imgur.com/TrTsyhq.png[/IMG]

so i don't know what's going on but hopefully that will help, thank you.

edit: more info, doing sudo gdisk -l:

```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 
```

i found and read some of this thread: [http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173) that discusses fixing gpt tables but it's not clear to me what actually got solved on how to fix it.

---

### Post by ubfan1 on 2015-07-01
Maybe you had something called "dynamic partitioning" for Windows -- that is proprietary and needs to be turned off before doing anything else.  Then once both OSes can agree on the partitions, you will be in better shape. (Also turn off the fast boot in the Windows power options, that prevents a normal boot from occurring). Boot repair might offer some fix, but I can't advise on its use.  Things tend to get better with each release, but 14.04 should be in pretty good shape concerning UEFI.

---

### Post by grahammechanical on 2015-07-01
Has anyone confirmed from the manufacturer's web site or some other source if this machine has a UEFI boot system motherboard but does not support secure boot?

> The UEFI 2.2 specification adds a protocol known as *secure boot*, which can secure the boot process by preventing the loading of drivers or OS loaders that are not [signed]("https://en.wikipedia.org/wiki/Public-key_cryptography") with an acceptable [digital signature]("https://en.wikipedia.org/wiki/Digital_signature").

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

The fact that the motherboard does not support secure boot should not be taken as meaning that Windows 8.1 was not installed in EFI mode and that the hard disk is not GTP and further more that certain recommended steps for installing Ubuntu alongside Windows 8 do not need to be taken.
> 
Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]
 
> To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. 
[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 
[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The initial problem seemed to be that the Ubuntu installer under the Something Else option did not see the unallocated space. Correct?

What do we see if we run the Ubuntu live session and load Gparted. Does Gparted see the unallocated space. Can it be used to create Ext4 partitions that the installer and the Something Else option will see?

Some principles I have learned for reading threads on this forum

1) Use Windows utilities to defrag Windows more than once, checking each time that Windows loads.
2) Use Windows utilities to resize/move/delete Windows partitions to create unallocated space.
3) have Windows repair disks
4) Use Linux utilities to create/resize/move/delete Linux partitions. e.g., Gparted.

I am wondering if Gparted from a live session will see something on that hard disk that the partitioner of the installer cannot see.

UEFI, GPT and Secure Boot are not usually problems when installing Linux. And have not been for a couple of years. Motherboard manufacturers that do not accurately comply with the UEFI specification are another matter.

Regards.

---

### Post by kimberly2 on 2015-07-01
> **ubfan1 said:**
> Maybe you had something called "dynamic partitioning" for Windows -- that is proprietary and needs to be turned off before doing anything else.  Then once both OSes can agree on the partitions, you will be in better shape. (Also turn off the fast boot in the Windows power options, that prevents a normal boot from occurring). Boot repair might offer some fix, but I can't advise on its use.  Things tend to get better with each release, but 14.04 should be in pretty good shape concerning UEFI.

hi, i've turned off fast boot. strangely, now doing sudo gdisk -l gave me basically nothing now. i'll check about the dynamic partitioning and report back.

---

### Post by kimberly2 on 2015-07-02
> **grahammechanical said:**
> Has anyone confirmed from the manufacturer's web site or some other source if this machine has a UEFI boot system motherboard but does not support secure boot?



[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

The fact that the motherboard does not support secure boot should not be taken as meaning that Windows 8.1 was not installed in EFI mode and that the hard disk is not GTP and further more that certain recommended steps for installing Ubuntu alongside Windows 8 do not need to be taken.
 


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The initial problem seemed to be that the Ubuntu installer under the Something Else option did not see the unallocated space. Correct?

What do we see if we run the Ubuntu live session and load Gparted. Does Gparted see the unallocated space. Can it be used to create Ext4 partitions that the installer and the Something Else option will see?

Some principles I have learned for reading threads on this forum

1) Use Windows utilities to defrag Windows more than once, checking each time that Windows loads.
2) Use Windows utilities to resize/move/delete Windows partitions to create unallocated space.
3) have Windows repair disks
4) Use Linux utilities to create/resize/move/delete Linux partitions. e.g., Gparted.

I am wondering if Gparted from a live session will see something on that hard disk that the partitioner of the installer cannot see.

UEFI, GPT and Secure Boot are not usually problems when installing Linux. And have not been for a couple of years. Motherboard manufacturers that do not accurately comply with the UEFI specification are another matter.

Regards.

thanks for the reply, so what do you suggest i do? i can try and get any info you need from the liveusb or windows.

should i be trying 15.04 instead or would that lead to more problems?

---

### Post by oldfred on 2015-07-02
Not sure why you are getting any partition list with fdisk unless using the very new versions of Ubuntu that have a very new version of fdisk that actually works with gpt.
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
There is such a thing as hybrid, which you want to avoid at all costs. It is used primarily by Mac which are UEFI, to boot Windows in BIOS Mode. But requires syncing the gpt & MBR partitions.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

In post #5 your gpt list looks like a normal Windows gpt partitioned drive. But not sure why you then had any list in fdisk other than the normal one large gpt partition which is to prevent you from using fdisk and corrupting a gpt drive.

What brand/model system?

Most often the reason you do not see Windows partition is that you left fast boot or the always on hibernation on. But could be that Windows still needs chkdsk, which it always needs after a resize, ot other partition issues.
      
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

Does Windows still boot?
In UEFI menu do you see both UEFI: and other boot options?
If a very new system, 15.04 may work slightly better as it has newer kernel & support software. But partition not seen issue will probably be the same.

Does gparted show NTFS partitions. There is a Windows reserved partition that gparted will show errors on as it is unformatted. But that is standard and it should not be formatted.
      
 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

With UEFI systems, you need to always boot in UEFI mode not BIOS/CSM/Legacy or else you may create issues. And do not use partition tools that are not gpt aware.

---

### Post by kimberly2 on 2015-07-02
> **oldfred said:**
> Not sure why you are getting any partition list with fdisk unless using the very new versions of Ubuntu that have a very new version of fdisk that actually works with gpt.
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
There is such a thing as hybrid, which you want to avoid at all costs. It is used primarily by Mac which are UEFI, to boot Windows in BIOS Mode. But requires syncing the gpt & MBR partitions.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

In post #5 your gpt list looks like a normal Windows gpt partitioned drive. But not sure why you then had any list in fdisk other than the normal one large gpt partition which is to prevent you from using fdisk and corrupting a gpt drive.

What brand/model system?

Most often the reason you do not see Windows partition is that you left fast boot or the always on hibernation on. But could be that Windows still needs chkdsk, which it always needs after a resize, ot other partition issues.
      
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

Does Windows still boot?
In UEFI menu do you see both UEFI: and other boot options?
If a very new system, 15.04 may work slightly better as it has newer kernel & support software. But partition not seen issue will probably be the same.

Does gparted show NTFS partitions. There is a Windows reserved partition that gparted will show errors on as it is unformatted. But that is standard and it should not be formatted.
      
 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

With UEFI systems, you need to always boot in UEFI mode not BIOS/CSM/Legacy or else you may create issues. And do not use partition tools that are not gpt aware.

hi, thanks for the response.

i noticed the pic i inserted into my post didn't get inserted inline, here it is: i.imgur.com/TrTsyhq.png it shows the Disks utility, which is one of the circumstances that DOES show the unallocated space I created.

so with regards to the brand/model -- it's a little weird, it's a refurbished, "unbranded" HP Pavilion Slimline... i guess because they refurbished it, they weren't allowed to sell it under HP's name anymore, so they covered all the HP stickers with these generic globe stickers and even sharpied out some mentions of HP! i hope that doesn't mean there's something wrong with it...

i turned fast startup off and checked to see if it would see the unallocated space but it still didn't. however, i didn't chkdsk after that, i'll try that now.

at this moment, windows is still booting.

sorry, what do you mean by uefi menu? do you mean the one when i start up the comp, or that one you access within windows by clicking restart while holding shift or something?

i assume that the windows disk management tool i used is "gpt aware" right?

thanks!

---

### Post by kimberly2 on 2015-07-02
ok, i also did chkdsk a bunch of times in a row. i don't know much about it, so this may be totally normal, but a few of the numbers it reports are changing each time i do it (though pretty slightly): <x> kb in <y> files, x kb in y indexes, x kb in use by the system, x kb available on disk, x allocation units available on disk. it says 0 kb in bad sectors and also says that it found no problems though. it also starts with "warning! f parameter not specified. running chkdsk in read-only mode"... is that bad?

anyway, booting back into the liveusb and trying the install again, when i get to the "something else" choice where it displays the partitions, it still just displays /dev/sda4 as one massive block.

also, since (i think) shutting off fast boot, when i do "sudo gdisk -l" in the liveusb, i get: gpt disk (gdisk) version 0.8.8. problem opening -l for reading! error is 2. the specified file does not exist!

okay, so i made what i might call a minor breakthrough, but i'm not gonna go through with it till i get the green light from someone more experience than me.

when i boot up, here's what it looks like:

[http://i.imgur.com/g873YFF.jpg](http://i.imgur.com/g873YFF.jpg)

the first thing is that f10 gives you the bios setup... but i thought there was no bios if it's uefi?

anyway, i'll get back to that in a second, but focus on f9, boot device options. if i select that, i get:

[http://i.imgur.com/5kKHZ0G.jpg](http://i.imgur.com/5kKHZ0G.jpg)

now, notice a couple things. first, my live usb stick shows up in two places: uefi, and legacy boot sources. all this time so far i've been doing the uefi one to get into the liveusb. but also, if i select the sata0 hard drive under legacy boot sources, it just boots my windows as usual...so what does THAT mean, is windows uefi or not??

anyway, since in the past i've been doing the uefi one, right now i tried the legacy one. it first showed me that little man with the keyboard symbol, then very slowly booted ubuntu (more slowly than when i did the uefi one). it gave me the (graphical, not CLI like the uefi one!) options to either try ubuntu or install it immediately. i decided to poke around in it without installing. gdisk gave the same thing ("error is 2"), but when i go to try and install it, it DOES give me the "install ubuntu alongside windows 8" option!

...but nothing can ever be easy. it asks me to allocate space to both, but only looks at /dev/sda5 and /dev/sda6, which are 10 and 6.5gb respectively. if i go to the "advanced partitioning tool", it has the same thing as before (the massive 900gb block as just one thing).

so that's interesting at the least.

back to the bios thing. if i do that, here are a few things.

system info:

[http://i.imgur.com/LZ6zoQS.jpg](http://i.imgur.com/LZ6zoQS.jpg)

secure boot (i thought that command i did in windows suggested i don't have that option...):

[http://i.imgur.com/bfzBSyt.jpg](http://i.imgur.com/bfzBSyt.jpg)

gives me this warning:

[http://i.imgur.com/5Gd2rFQ.jpg](http://i.imgur.com/5Gd2rFQ.jpg)

but then gives me these options:

[http://i.imgur.com/JAj5SxA.jpg](http://i.imgur.com/JAj5SxA.jpg)

i get the feeling the key is here but i don't know what to do. any ideas? thanks!


ok, so i did some more poking around and it gets more confusing (for me, but maybe it will make a lot of sense to you). here are a bunch of pictures, because i can't screenshot/copy during boot:

---

### Post by ubfan1 on 2015-07-02
I think the "refurbished" is the key here.  All "pre-installed" Win 8 machines are UFEI mode on a gpt disk.  What you have  looks like Win 8 was installed in legacy mode.  This means Ubuntu should be installed in legacy mode so both may be booted without having to switch modes.  Not sure what's with the disk reports.  I'd use   sudo gdisk -l /dev/sda  to get a report down to the bytes (parted  does not seem to work as the man pages advertise for selecting units).  That way, you can copy them and restore if necessary (like maybe recreating the gpt partition table to fix any claimed damage).  Maybe you already did fix it.

---

### Post by oldfred on 2015-07-02
I think I agree with ubfan1.
Windows reinstall in BIOS mode converts a gpt drive to MBR(msdos), but does it incorrectly.
It leaves the backup gpt partition table. And then Linux tools see both gpt & MBR and only assume you want to erase drive to clean it up.

Either way it needs to be housecleaned. Either drive must be fully UEFI/gpt or BIOS/MBR.
You can use fixparts to erase backup gpt data.

I do not know how to tell from inside Windows whether you have booted in BIOS or UEFI mode.

You can run Boot-Repair's summary report and it will show details, but may just show both?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
If Windows is booting in BIOS mode, you need to run this:
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by kimberly2 on 2015-07-03
> **oldfred said:**
> I think I agree with ubfan1.
Windows reinstall in BIOS mode converts a gpt drive to MBR(msdos), but does it incorrectly.
It leaves the backup gpt partition table. And then Linux tools see both gpt & MBR and only assume you want to erase drive to clean it up.

Either way it needs to be housecleaned. Either drive must be fully UEFI/gpt or BIOS/MBR.
You can use fixparts to erase backup gpt data.

I do not know how to tell from inside Windows whether you have booted in BIOS or UEFI mode.

You can run Boot-Repair's summary report and it will show details, but may just show both?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
If Windows is booting in BIOS mode, you need to run this:
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

thanks for the replies guys. i suspect w8 is booting in bios mode -- because in the pic i included above (of the boot sources), the HD that loads w8 if i select it is under the "legacy boot sources" section, and nothing's really under uefi. also, there's some sort of uefi menu you can access, like in this article: [http://www.howtogeek.com/175649/what-you-need-to-know-about-using-uefi-instead-of-the-bios/](http://www.howtogeek.com/175649/what-you-need-to-know-about-using-uefi-instead-of-the-bios/)

i can get as far as the "troubleshoot->advanced options" menu, but mine has everything except the "uefi firmware settings" tile. so this further reinforces that it is installed with legacy.

in a way it is comforting that mine may be a special case, because it means i'm not just missing something obvious. but it's also awful, because now i have to do this stuff.

in my "secure boot config" pic above, what do you think about the fact that "fast boot" is enabled there, even though i disabled it from w8? is it like, having it enabled here allows you have it at all, but having it disabled in windows should still disable it?

i'm kind of confused now. if w8 is installed in bios/legacy mode, then what's the issue and why isn't ubuntu seeing the right stuff when i boot it in legacy mode?

the weird thing is that it IS seeing that windows is there when i boot it in legacy mode (see above) but it still doesn't see the unallocated space. do you think using fixpart to remove the gpt stuff would actually fix that and make it see that space?

what exactly is the Disks utility doing differently that it (and mostly none of the other utilities) sees the unallocated space from within ubuntu?

---

### Post by oldfred on 2015-07-03
Windows 8 has fast startup which is always on hibernation. You must turn that off if dual booting.

Fast Boot is an UEFI setting where it does not check system for new hardware and assumes it is the same. That speeds boot a lot, but can lead to issues where you cannot get into UEFI to change settings. Best to turn it off at least for now.

My UEFI motherboard has several fast boot settings. One for warm reboot, one for cold power down restart & timing on fast boot setting. So I set cold boot to normal, fastboot off & reboot to fastboot but with a 3 sec delay so I have a chance to press del key and get into UEFI to change a setting.

Not sure if disks then is recognizing drive as both MBR & gpt as in hybrid?

Whatever you do, I would fully backup Windows. Then even in worse case you can restore it.
My new Dell SFF system had Dell backup, Windows backup & I did a full backup with Macrium. But that was 2 flash drives & 5 DVDs.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by kimberly2 on 2015-07-04
> **oldfred said:**
> Windows 8 has fast startup which is always on hibernation. You must turn that off if dual booting.

Fast Boot is an UEFI setting where it does not check system for new hardware and assumes it is the same. That speeds boot a lot, but can lead to issues where you cannot get into UEFI to change settings. Best to turn it off at least for now.

My UEFI motherboard has several fast boot settings. One for warm reboot, one for cold power down restart & timing on fast boot setting. So I set cold boot to normal, fastboot off & reboot to fastboot but with a 3 sec delay so I have a chance to press del key and get into UEFI to change a setting.

Not sure if disks then is recognizing drive as both MBR & gpt as in hybrid?

Whatever you do, I would fully backup Windows. Then even in worse case you can restore it.
My new Dell SFF system had Dell backup, Windows backup & I did a full backup with Macrium. But that was 2 flash drives & 5 DVDs.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

hi thanks for the response again.

sorry, i'm not sure what you mean by "w8 has a fast boot that is always on hibernation". what do you mean by "always on hibernation"? i assume you also mean the fast boot whose option is found in the power options like this: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

if so, i've turned that off a while ago.

when you said "fast boot is a uefi setting..." you were still talking about that one?

when you said "My UEFI motherboard has several fast boot settings" did you mean still the windows one, or the one i found as in this picture? [http://i.imgur.com/JAj5SxA.jpg](http://i.imgur.com/JAj5SxA.jpg)

the backup shouldn't be too hard because the system has literally nothing on it except the OS.

so your suggestion right now is basically to backup, then use fixparts?

thank you!

---

### Post by oldfred on 2015-07-04
Backup is always a good idea, if your backup is not current.

Fast startup is a Windows setting. That is just hibernation.
Fast boot is a UEFI setting as you show in your picture. That can cause issues as system may boot so fast that you cannot get back into UEFI. 
Design of fast boot seems to be that you are supposed to get into UEFI from Windows. But if Windows breaks, then you may not be able to get into UEFI. Most revert to a standard boot on a total cold boot or after power shutdown. But a few do not and users have not been able to get into UEFI to fix settings. Grub now also has a setting to get into UEFI, that may work for most systems.

---

### Post by kimberly2 on 2015-07-12
> **oldfred said:**
> Backup is always a good idea, if your backup is not current.

Fast startup is a Windows setting. That is just hibernation.
Fast boot is a UEFI setting as you show in your picture. That can cause issues as system may boot so fast that you cannot get back into UEFI. 
Design of fast boot seems to be that you are supposed to get into UEFI from Windows. But if Windows breaks, then you may not be able to get into UEFI. Most revert to a standard boot on a total cold boot or after power shutdown. But a few do not and users have not been able to get into UEFI to fix settings. Grub now also has a setting to get into UEFI, that may work for most systems.

alright, i've been pretty busy but i'm gonna try backing it up and fixing it. i highly suspect that it will mess things up and i'll end up just nuking the HD and doing a clean install anyway, but it's worth a shot. i'll report back either way. thanks for the help.

---

### Post by kimberly2 on 2015-07-12
> **oldfred said:**
> Backup is always a good idea, if your backup is not current.

Fast startup is a Windows setting. That is just hibernation.
Fast boot is a UEFI setting as you show in your picture. That can cause issues as system may boot so fast that you cannot get back into UEFI. 
Design of fast boot seems to be that you are supposed to get into UEFI from Windows. But if Windows breaks, then you may not be able to get into UEFI. Most revert to a standard boot on a total cold boot or after power shutdown. But a few do not and users have not been able to get into UEFI to fix settings. Grub now also has a setting to get into UEFI, that may work for most systems.

hi, so some progress i think. hopefully someone sees this soon so i can proceed.

i used fixparts (off a liveusb) and like he says on his webpage for it: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

> FixParts checks the validity of the partitions it finds on your disk and will automatically (and silently) make adjustments for certain problems it finds. Thus, you may discover that your partition table is fine at this point. It's also possible that you'll see some changes in primary vs. logical status, or even omitted partitions. 

i'm pretty sure this was the case for me. i did sudo fixparts /dev/sda, and then had to hit w to write it, then q to quit.

now the unallocated space shows up pretty much everywhere, gparted for example.

w8 still boots, so that's good.

even now though, and i have no idea what this means, when i go into the boot menu, the liveusb still appears in uefi and legacy modes.

if i go into uefi mode and try to install, when i get to the "installation type" (where you choose what partition/etc to install to), it only has the "something else" choice, that basically leads you to gparted.

if i boot with legacy mode instead, it has both "install ubuntu alongside windows 8" and "something else". if i choose "alongside", i get this:

[http://i.imgur.com/KRhKkl2.jpg](http://i.imgur.com/KRhKkl2.jpg)

if i choose "something else" instead (this pic is for booting during legacy mode, but i'm pretty sure it looks the same if i boot into uefi): [http://i.imgur.com/6n0UDjA.jpg](http://i.imgur.com/6n0UDjA.jpg)

so you can see the free space there.

so, what should i do? do you think the stuff that it says will happen if i choose "alongside w8" is fine, or would it mess stuff up?

one person has told me that i should choose "something else", then choose to install to the free space, and choose /dev/sda for the "device for boot loader installation", and it will take care of the rest.

i think i've almost got it, any help would be much appreciated! thank you!

---

### Post by ubfan1 on 2015-07-12
I generally use the "something else", creating a root and a swap at the minimum, which looks just like the "alongside" picture you posted.  When you do it yourself, you can choose to make a separate /home or data partition, so you files may be separated from the rest of the operating system, but that's not required, and you risk leaving the root too small.

---

### Post by ubfan1 on 2015-07-12
I generally use the "something else", creating a root and a swap at the minimum, which looks just like the "alongside" picture you posted.  When you do it yourself, you can choose to make a separate /home or data partition, so you files may be separated from the rest of the operating system, but that's not required, and you risk leaving the root too small.

---

### Post by kimberly2 on 2015-07-13
> **ubfan1 said:**
> I generally use the "something else", creating a root and a swap at the minimum, which looks just like the "alongside" picture you posted.  When you do it yourself, you can choose to make a separate /home or data partition, so you files may be separated from the rest of the operating system, but that's not required, and you risk leaving the root too small.

hi thanks for the response. yeah i don't really care about having /home be a separate partition from / anymore. i'd be fine with just / and swap.

ok so i guess here's where i'm confused/worried. if you look at the 2nd pic (of what "something else" shows), sda1 is the windows bootloader (~1gb), sda2 is the windows C partition (~492gb), then there's the free space which i made for ubuntu (~491gb), and then there's sda3 (~15gb) which is the windows recovery partition. i don't really know how that partition works (like if it will still work once i install ubuntu and mess with the mbr and such), but i guess i'd like to keep it if i can. here's the thing though. before i did the fixparts thing, when i booted the liveusb in legacy mode, i'd *also* get the "alongside w8" option, but it wasn't seeing the free space like it is now (it saw C and free space as the one big block it started as for some reason...), it was seeing the 15gb windows recovery partition, sda3.

so i guess i'm worried now that if i do the "alongside w8" one now it might still do that, because before it brought me to a interface where i could divide up that 15gb into ubuntu/windows space, but now i don't get that window (in this pic [http://i.imgur.com/KRhKkl2.jpg](http://i.imgur.com/KRhKkl2.jpg) it says "if you continue the changes below will be written to the disks"). so i'm not really sure if it's talking about the free space or maybe the windows recovery partition.

i'm also not really clear on what it says in the "alongside w8" dialog, it says:

> the following partitions are going to be formatted:
partition #5 of SCSI3 (0,0,0) (sda) as ex4
partition #6 of SCSI3 (0,0,0) (sda) as swap


but why is it #5 and #6? it seems like so far there are only 3, and the free space, but i thought it would be turning the free space into them...

any help for a confused person? thanks!

---

### Post by ubfan1 on 2015-07-13
Remember this is an msdos partitioned disk, so only four primary partitions -- not enough.  So one primary get made into an extended over all the free space (sda4).  Then you are allowed to make logical partitions inside the extended, which would be sda5 and sda6.  That's what is expected and necessary in this case.  Your sda5 and sda6 should together fill the free space.

---

### Post by kimberly2 on 2015-07-13
> **ubfan1 said:**
> Remember this is an msdos partitioned disk, so only four primary partitions -- not enough.  So one primary get made into an extended over all the free space (sda4).  Then you are allowed to make logical partitions inside the extended, which would be sda5 and sda6.  That's what is expected and necessary in this case.  Your sda5 and sda6 should together fill the free space.

awesome. so you think that, if i just want the simple / and swap partitions, the thing it's gonna do for "alongside windows 8" should be good?

thanks!

---

### Post by kimberly2 on 2015-07-13
hi everyone, it appears to have worked. so no one has to go through this awfulness again, i'll try and quickly summarize what i learned here:


[LIST=1]
[*]if you buy a "debranded" computer (like from newegg), apparently they somehow install w8 using mbr/legacy/bios as opposed to what's currently used, gpt/uefi (correct me if i'm wrong about that). so that creates problems. most notably, when i shrunk my c drive in w8 (to create free/unallocated space for ubuntu), that free space didn't appear in almost any of the disk analyzers (gparted, fdisk, etc), so this naturally created a problem for dual booting (it just appeared as the original huge block).
[*]to make it see this space as a separate block of memory, i used fixparts. i hit 'y' the first time, and then basically just 'w', and i'm pretty sure that fixed it.
[*]even after doing this, i still had the option (at choose boot source menu) to boot my liveusb as uefi or legacy. if i did it as uefi, when i got to the window where you choose how to install ubuntu (with regarts to memory and partitions), it did *not* give me the "alongside windows 8" choice, but it *did* see the free space in the gparted type display.
[*]however, if i booted in legacy mode, it gave me the "alongside w8" option and that seemed correct, and simpler, so i chose that.
[/LIST]

and here i am! they both boot nicely. wheeeeeee.

thanks for the help, oldfred.

---

