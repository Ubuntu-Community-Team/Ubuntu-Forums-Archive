---
title: "Online Update to 10.04: loss of Windows Boot"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by MikeB007 on 2010-05-02
Machine: Win2000 Pro, AMD64 Athlon 2GHz, 2x80Gb HD, 2 GB RAM

Symptoms: Running 9.10 with dual boot no probs for ~ 1 year.  Decided to upgrade online via synaptic to 10.04.  Upgrade went well no warnings, etc.  On reboot all OS options present in Grub BUT clicking on Win2000 causes the screen to blank temporarily and then return to the Grub menu ie. no functioning Win2000 boot option.  Ubuntu 10.04 boot yields blank screen with flashing cursor, a sudden stream of IO error messages (can't capture it but the lines look identical) then screen flickers and I'm at the purple log in screen and everything proceeds perfectly from there.

Observations:  For the first time on any of my ubuntu installs (i've been using since 8.04 always installing from CD though) grub installation asked where I wanted it.  In fact, the screen shows all devices with check boxes wth which to make my choice.  That is sdb, sdb1, sdb2, ... , sda, sda1, sda2, ...
There was a help message that says that if in doubt install on _all_.  Being in doubt I checked all the boxes: sdb, sdb1, etc.  I noted in the message streams that followed after i continued that some lines had "... this is BAD ..." but since it was all rolling along very quickly no idea exactly _what_ was bad.

Action:  I am not a linux newb but I am a grub newb.  I fished the forums and googled only to come completely confused about what the problem might be or what to do.  Example: have i overwritten my win bootloader? is my mbr corrupted? if i remove grub what will happen?  if i remove and reinstall grub will i get windows booting back?  if i use my win2000 install CD will it overwrite my whole disk (as many warn) or can i just fix the mbr?  if I do the latter what order do i ie use fix mbr then fix boot?  The info i've come across so far either doesn't address what happened to me, deals with other OSs (XP, Vista), or is applied to earlier editions of grub/ubuntu.

Right now I have not found a clear step by step that addresses my circumstance.  Would anyone be able to provide some guidance? I need the windows boot to run some software (Matlab) that btw will not work with XP/Vista (hence the reason i still have win2k).

---

### Post by MikeB007 on 2010-05-02
Ran Boot Info Script.  Results attached.

---

### Post by MikeB007 on 2010-05-02
fdisk output is:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0043356d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5503    44202816    7  HPFS/NTFS
/dev/sdb2            5504        9728    33937312+   f  W95 Ext'd (LBA)
/dev/sdb5            8454        9728    10241406    c  W95 FAT32 (LBA)
/dev/sdb6            5504        8325    22667652   83  Linux
/dev/sdb7            8326        8453     1028128+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8cbe9d86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

---

### Post by vinod_home on 2010-05-02
I see a few people having the same issue. Dont know where the problem is, but I am guessing its got to do with grub2. Hope someone gives a procedure to fix this soon. 

Did you install grub on that sdb1 partition?

---

### Post by oldfred on 2010-05-02
You installed grub to the windows partition overwriting the windows boot loader.

    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 88749501 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Where in the update instructions does it say to install grub everywhere? Several have commented that is the case and I think we need to post that as a bug even though it is an error in instructions and not a software bug.

---

### Post by MikeB007 on 2010-05-02
As I recall, at one point you are asked where you want to install grub.  As mentioned, all partitions are shown.  Where the direction is I don't recall but it is affiliated with that page so maybe a drop down help or something written in the guidance as to what to do on that page.  But I can assure you it _is_ written there.  As I said, I don't recall ever being asked where I wanted grub installed so I read whatever guidance was provided and adhered to it.

---

### Post by djchandler on 2010-05-02
People losing the other OS on a hard drive may want to read this:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

There's still no link to this report that I can find on Ubuntu Forums (until now).

[https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765](https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765)

Most of the beta testing I did was on a dual-booting laptop. This last installation was created using the RC ISO. This has to be something that crept into the mix between the RC and the final release.

---

### Post by AzT3K on 2010-05-02
I had this problem too - was my own fault of course, hopefully I can shed some light on this for you....


When you upgrade from 9.10 to 10.04 grub installation prompts you to select a drive to install it on.  It suggests if there is any doubt install to all.  This not what you want to do.  

What you should do is find the disk that has ubuntu installed on it eg /dev/sda1 and install grub to /dev/sda.  this is because grub installs to the Master Boot Record of a given disk rather than the install partition.  If you try to set up grub manually it throws an error complaining if u try to install it to a partition.

However that being said - there is also a bug in grub 2 which prevents update-grub from finding windows installs -> at least on my system.  Here's what I did to fix the problem -> depending on what the exact problem is:

------------------------------------
If your system isn't booting at all 
------------------------------------

1. follow the steps in the "To make windows work again" section of this post
2. reinstall grub by following the instructions in the "Reinstalling grub from the live cd" section of this post
3. manually add a menu entry to ur /boot/grub/grub.cfg file by following the steps in the "Manually adding entries to ur grub.cfg file" section of this post

----------------------------
If your ubuntu boots fine but you cant see windows in your grub boot menu
-----------------------------

NB: this has to be done from ur ubuntu install if you can't boot into that then you need to reinstall grub by following the instructions in the "Reinstalling grub from the live cd" section of this post

In your terminal type

> sudo update-grub

if that doesn't find the windows install then u may have to manually add it to ur /boot/grub/grub.cfg file by following the steps in the "Manually adding entries to ur grub.cfg file" section of this post.

------------------------------------------
Manually adding entries to ur grub.cfg file
-------------------------------------------

In the terminal type:

> sudo gedit /boot/grub/grub.cfg

Add this to end of your grub.cfg file (presuming ur windows install is on sda2 and the 100mb system reserved partition is on sda1, if you have a version of windows older than 7 i dont think windows boots from a separate partition from the one that it installs on, so in that situation ud prob point the boot loader to sda2 aka hd0 partition 2 rather sda1 aka hd0 partition 1):

> menuentry "Microsoft Windows 7 Ultimate (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set {UUID}
	drivemap -s (hd0) ${root}
	chainloader +1
}

Where {UUID} is the UUID for the drive in question i.e. (hd0,1) aka sda1 for me it something like "f8be5fe4-34d1-48f2-a8ce-3ce4c425c07b" so the line looked like:

> menuentry "Microsoft Windows 7 Ultimate (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f8be5fe4-34d1-48f2-a8ce-3ce4c425c07b
	drivemap -s (hd0) ${root}
	chainloader +1
}

That works for me however i managed to break my windows boot loader as well so this what you do to fix that:

----------------------------
To make windows work again
-----------------------------

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 

> 
BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


I'll add a comment to this say u prob only need to run in this order to get windows booting again:

> 
BootRec.exe /FixMbr
BootRec.exe /FixBoot
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


And this will make your windows install work again, but it overwrites grub so you will need to reinstall grub to boot into ubuntu which u can do many ways, but this is the way suggested for 10.04:

----------------------------------
Reinstalling grub from the live cd
------------------------------------

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

> sudo fdisk -l

If the user isn't sure of the partition, look for one of the appropriate size or formatting.

Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.

Mount the partition containing the Ubuntu installation.

sudo mount /dev/sd''xY'' /mnt

Example: 

> sudo mount /dev/sda1 /mnt 

Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot

Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

sudo grub-install --root-directory=/mnt/ /dev/sdX

Example:

> sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot

Refresh the GRUB 2 menu with 

> sudo update-grub


If that doesn't re-install grub for you may have to try one of the other methods here : [https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)

The problem with re-installing grub is that it still couldn't find my windows install so i had to manually add the entry afterwards as per the manually adding entry to grub.cfg section

Hopefully this helps :)

---

### Post by Kuoi on 2010-05-03
This did it for me !! THANKS

> ----------------------------
To make windows work again
-----------------------------

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:

Quote:
BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub
chkdsk /r
BootRec.exe /FixBoot #updates PBR partition boot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
I'll add a comment to this say u prob only need to run in this order to get windows booting again:

Quote:
BootRec.exe /FixMbr
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
And this will make your windows install work again, but it overwrites grub so you will need to reinstall grub to boot into ubuntu which u can do many ways, but this is the way suggested for 10.04:

----------------------------------
Reinstalling grub from the live cd
------------------------------------

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

Quote:
sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting.

Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.

Mount the partition containing the Ubuntu installation.

sudo mount /dev/sd''xY'' /mnt

Example:

Quote:
sudo mount /dev/sda1 /mnt
Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot

Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

sudo grub-install --root-directory=/mnt/ /dev/sdX

Example:

Quote:
sudo grub-install --root-directory=/mnt/ /dev/sda
Reboot

Refresh the GRUB 2 menu with

Quote:
sudo update-grub

If that doesn't re-install grub for you may have to try one of the other methods here : [https://help.ubuntu.com/community/Gr...talling](https://help.ubuntu.com/community/Gr...talling) GRUB 2

The problem with re-installing grub is that it still couldn't find my windows install so i had to manually add the entry afterwards as per the manually adding entry to grub.cfg section

Hopefully this helps 

---

### Post by MikeB007 on 2010-05-04
We can call this solved but embarrassingly I can only give a partial explanation of what I did.  

I used testdisk.  Somewhere I found an excellent guide that walked me through the process of downloading testdisk, installing it, and fixing my Grub2 problem.  It worked perfectly.  But it was late, I was tired, crashed woke up and I have no idea what exactly I did.  Total "senior moment".

I was certain I'd bookmarked the site but can't find the link in my browser history.  I can retrace my steps in my terminal by calling up my command history but it stops after "sudo testdisk".  But maybe this hint will help.

Thanks for all the replies.

---

### Post by oldfred on 2010-05-04
In my post #5 is a link that uses testdisk to repair windows. That probably was the instructions you used. 
Many of us are recommending that page which seems to work for most, if that does not work the windows fixboot command.

---

### Post by MikeB007 on 2010-05-05
Yes!  Thanks.

---

### Post by ashokranade on 2010-05-11
[LEFT]Az3Tk procedure worked for me. Thanks a lot
[/LEFT]

---

### Post by divastauras on 2010-05-12
Thanks a lot for this wonderful post, the fixboot command worked for me I am able to recover my lost Windows 7, and as per the instructions mentioned I was expecting that the grub will need to be reinstalled from the live cd, but to my surprise Ubuntu 10 also got booted without any difficulties.

Thanks again for the post

---

