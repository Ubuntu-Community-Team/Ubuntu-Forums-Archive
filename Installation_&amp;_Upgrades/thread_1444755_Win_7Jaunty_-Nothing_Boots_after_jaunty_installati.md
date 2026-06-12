---
title: "Win 7/Jaunty -Nothing Boots after jaunty installation"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by nickhopkins07 on 2010-04-01
Hi Guys,
 
I'm sure this has been answered already, I've had a search, but given I don't really know what I've done, I'm not sure what to search for!
 
I've got a laptop with Win 7 on it, and I wanted to install Jaunty as a dual boot to further my understanding of Ubuntu, and I think I've screwed up big time :-( I've read up prior, but I've still managed to mess up somehow.
 
So I had two partitions one with my Win 7 one and an empty one, so I downloaded jaunty and used netbootin to create a bootable USB stick and booted into Jaunty, ran the install, followed the install process, chose the empty partition for Jaunty, and then on the last page (before clicking the install button) I clicked advance, and chose the same partition for the Ubuntu's version of MBR to be installed to, so as not to get in the way of MBR, or so I thought.
 
Install went through ok, but now when I start up the computer I dont get a dual boot screen, Win 7 starts right up, although it doesn't finish, the Win 7 splash screen appears, then blue screens (disapears to quick to read) and thats that! I've tried using the Win 7 repair disk and the bootrec.exe functions, but to no avail, also cant get into Win 7 in safe mode.
 
So the only way I can get anything out of the laptop at the moment is to use the bootable USB stick I created.
 
Can someone please outline what they think I may have done, and if it's fixable? I'll start from scratch and re-install if need be, but I'd rather not to be honest, as I see it I've have both the OS's I want installed, i just need a way to select them/load them.
 
Many thanks in advance.
 
Nick

---

### Post by oldfred on 2010-04-01
Windows does not do other operationing systems, there are some workaround and third party boot loaders that will let you think you are still useing windows boot but are not.

Grub is the flexible boot loader that will let you choose to boot Ubuntu or windows. The chainboot entry of grub into the PBR can only be booted from another boot loader. Used primarily when you have many operating systems.

To install grub legacy (0.97) or reinstall windows boot loader if you ever want to go back.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by coffeecat on 2010-04-02
> **nickhopkins07 said:**
> I clicked advance, and chose the same partition for the Ubuntu's version of MBR to be installed to, so as not to get in the way of MBR, or so I thought.

That was your mistake, I'm afraid. Grub stage 1 does need to go to the MBR, replacing the Windows MBR. 

Anyway - have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Boot up with your Ubuntu USB stick. You should be able to download and run the script, and post the RESULTS.txt file all from the live USB session. The RESULTS.txt file gives a load of useful information, including the state of the Windows boot code on the Windows partition(s). With that information we'll know where to reinstall grub so that you can boot into Ubuntu, and hopefully give us a clue why bootrec.exe hasn't helped you.

---

### Post by nickhopkins07 on 2010-04-02
OldFred/CoffeeCat,
 
Thank you both for your replies, to update on my problem;
 
I followed the link in Oldfreds post, and using that I've managed to successfully restore Grub. So currently when I boot up I am now faced with a dual boot screen, from here I can happily start up the installed edition of 9.04, wonderful.

I'm still having the same problem with Win7 though, If I chose to load windows from the dual boot screen, it starts the process, then blue screens and the laptop restarts, I've tried repairing it with the Win 7 rescue cd, but to no avail. What is interesting/confusing is in the dual boot screen, windows is listed Vista rather win 7, which seems odd to me!

When I boot into Jaunty and look at the drives, I have one partition with Win 7 on it, which when i browse to it seems fine, all the folders etc you'd expect to be there are. I have another partition called 'SYSTEM' which I beleive to house the original MBR on, and a third partition 'Filesystem' with all the Jauty stuff on.

It's been suggested on the other thread my best option is to re-install Win 7, which if I have to I will, my only problem is my laptop was supplied with the licence only, and no disk, so it's going to cost me, and I think Microsoft have enough money as it is, without me having to pay twice for Win 7!
 
CoffeeCat, I'll run your boot script as suggested and post the results, many thanks.

---

### Post by coffeecat on 2010-04-02
> **nickhopkins07 said:**
> CoffeeCat, I'll run your boot script as suggested and post the results, many thanks.

I'll look at it when you've posted it. The list of partitions you mention is, I guess, from the Places menu. That won't be complete. There may be a hidden Windows restore partition from which you could reinstall W7 if necessary. But let's see.

---

### Post by nickhopkins07 on 2010-04-02
Right, I've run the script and here's the reults, I've quoted them to try and make them easier to read from the rest of the post, and I'm not sure how to stop the ( 8 ) turning into smilieys:
 
>  Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
File system: ext2
Boot sector type: Grub
Boot sector info: Grub 0.97 is installed in the boot sector of sda1 and 
looks at sector 7110719 of the same hard drive for the 
stage2 file. A stage2 file is at this location on 
/dev/sda. Stage2 looks on partition #1 for 
/boot/grub/menu.lst.
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /bootmgr /Boot/BCD
sda3: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe
sda4: _________________________________________________________________________
File system: 
Boot sector type: -
Boot sector info: 
Mounting failed:
mount: unknown filesystem type ''
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3095cd7a
Partition Boot Start End Size Id System
/dev/sda1 63 27,374,759 27,374,697 83 Linux
/dev/sda2 * 31,459,328 31,664,127 204,800 42 SFS
/dev/sda3 31,664,128 625,137,663 593,473,536 42 SFS
/dev/sda4 625,137,664 625,140,399 2,736 42 SFS
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 1025 MB, 1025507328 bytes
1 heads, 32 sectors/track, 62592 cylinders, total 2002944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ba8e73f
Partition Boot Start End Size Id System
/dev/sdb1 * 32 2,002,943 2,002,912 b W95 FAT32
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/sda1 a3b2496a-b3f5-4f3a-b219-51e841a5f52d ext2 
/dev/sda2 DA9676039675E105 ntfs SYSTEM 
/dev/sda3 F65A78085A77C441 ntfs 
/dev/sdb1 F8D9-5ABF vfat CORSAIR 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
/dev/sda1 / ext2 (rw,errors=remount-ro)
/dev/sr0 /media/Repair disc Windows 7 32-bit udf (ro,nosuid,nodev,uhelper=hal,uid=1000)
/dev/sdb1 /media/CORSAIR vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
 
=========================== sda1/boot/grub/menu.lst: ===========================
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
# Pretty colours
#color cyan/blue white/blue
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
## DO NOT UNCOMMENT THEM, Just edit them to your needs
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a3b2496a-b3f5-4f3a-b219-51e841a5f52d ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=a3b2496a-b3f5-4f3a-b219-51e841a5f52d
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
## ## End Default Options ##
title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid a3b2496a-b3f5-4f3a-b219-51e841a5f52d
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=a3b2496a-b3f5-4f3a-b219-51e841a5f52d ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic
quiet
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid a3b2496a-b3f5-4f3a-b219-51e841a5f52d
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=a3b2496a-b3f5-4f3a-b219-51e841a5f52d ro single
initrd /boot/initrd.img-2.6.28-11-generic
title Ubuntu 9.04, memtest86+
uuid a3b2496a-b3f5-4f3a-b219-51e841a5f52d
kernel /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
chainloader +1
 
=============================== sda1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=a3b2496a-b3f5-4f3a-b219-51e841a5f52d / ext2 errors=remount-ro 0 1
/dev/sdb /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
=================== sda1: Location of files loaded by Grub: ===================
 
3.6GB: boot/grub/menu.lst
3.6GB: boot/grub/stage2
3.6GB: boot/initrd.img-2.6.28-11-generic
3.6GB: boot/vmlinuz-2.6.28-11-generic
3.6GB: initrd.img
3.6GB: vmlinuz

 
It's a bit over my head to interprut them, hopefully it all means something to you though!?
 
Thanks again

---

### Post by coffeecat on 2010-04-02
> **nickhopkins07 said:**
> Right, I've run the script and here's the reults, I've quoted them to try and make them easier to read from the rest of the post, and I'm not sure how to stop the ( 8 ) turning into smilieys:

Tip 1 - when posting code like this, under the message box in 'Additional Options', tick the 'Disable smilies in text' box.

Tip 2 - Use [noparse]```

```[/noparse] tags instead of quote tags. Easy way is to click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button, instead of the [IMG]http://ubuntuforums.org/images/editor/quote.gif[/IMG] one.

Anyway, to your problem.

First:

> sda1: __________________________________________________  _______________________
File system: ext2Oops, and oops! Beginner's mistakes, but worth learning from. You've installed to sda1, the first primary partition which was probably once the manufacturer's recovery partition. Which means that you have no way of reinstalling Win7. Except that if we can get you booting into W7 again, there may be a utility to create a restore DVD - possibly, but this often relies on the presence of the recovery partition. Failing that, the laptop manufacturer may be prepared to sell you a restore DVD, but it won't be cheap. What is the make and model of the laptop, by the way?

Second mistake is that you chose ext2 as the filesystem. I guess you went into the 'manual' option at the partitioning stage and ext2 was the first on the list. It wasn't a recommendation. Ext2 is the old non-journalled predecessor to ext3, which would probably be the best choice for Jaunty. All is not lost, though. Jaunty will work just fine with ext2, but ext2 is much more prone to corruption in the event of an unclean shutdown. It's possible to convert the filesystem to ext3, but you'd also need to edit a system file. Let's come back to that[B].

Windows[/B]

I can't see anything that would tell us why Windows won't boot. You mention...

> I've tried using the Win 7 repair disk and the bootrec.exe functions,What exactly is that? Is it the Recovery disc that you can prepare from Windows 7, or  download here?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Rather than running bootrec.exe from the command prompt, have you tried the 'Startup Repair' choice from the Recovery Options? And/or have you tried to 'chkdsk' the two Windows partitions from the command prompt of the repair disc?

Last thing - don't worry about grub misidentifying Windows 7 as Vista. That version of Ubuntu (and grub) was released before W7. The grub functionality for W7 is the same as for Vista. We can edit the grub menu later if it worries you. Later versions of Ubuntu use the newer grub2 which seems better at identifying Windows 7. Um - usually! On my Acer laptop, the two Windows 7 partitions are identified correctly, but the recovery partition appears as 'Vista' on the grub menu. :?

---

### Post by nickhopkins07 on 2010-04-02
CoffeeCat, first up, thanks for your continued quick replies, it really is appreciated.
 
I'm pretty sure if we can get the current install of Win 7 there is a pre-installed peice of software that will let me create a recovery disk, I think you're probably right that where I've installed Jaunty is where there was originally a recovery partition, lesson learnt! The laptop is a Samsung R580. If a re-install of Win 7 is my only option, i should be able to buy a media only version via my works Software Re-sellers, and just use the license key on the base of the laptop, I hope anyway!
 
Anyway hoping it wont come to that. And you're right about Ext2, lesson No.2 learnt!
 
With regards to the windows 7 disk, it is indeed that download, and burnt to disk on another laptop. I've run the Startup Repair, but it doesn't appear to find anything, at least anything it can fix I guess. When I go into the command line via the Win 7 repair disk, I'm put at location 'x:\', if I run chkdsk, it's nearly instant between start and finish, I believe it's only checkng the x:\ partition. If I click on the 'Load Drivers'  button I'm given a Windows style GUI to browse to 'My computer', in there it only see's the X:\ partition, there's no partition for C:\ or the one Jaunty is installed on. But for all I know that's normal. But it does seem as if Chkdsk from that command line isn't actually checking c:\ where win 7 is installed.
 
I guess something that might help shed some light is if the blue screen that appears briefly, stayed on the screen longer so I could read what it was telling me. Do you think it would be recorded somewhere on the HDD? That I could maybe browse to via the Jaunty install.
 
I can't see why the Jaunty installation would have touched the partition Win 7 is o, and hence that Win 7 could be damaged in anyway.

---

### Post by coffeecat on 2010-04-02
> **nickhopkins07 said:**
> If a re-install of Win 7 is my only option, i should be able to buy a media only version via my works Software Re-sellers, and just use the license key on the base of the laptop, I hope anyway!

Maybe. One problem is that with laptops, there are all sorts of weird and wonderful bits of hardware that need the manufacturer's drivers. Even with a regular Window install DVD you can have an "interesting" time.

> **nickhopkins07 said:**
> When I go into the command line via the Win 7 repair disk, I'm put at location 'x:\', if I run chkdsk, it's nearly instant between start and finish, I believe it's only checkng the x:\ partition.

Yes, I believe that if you run chkdsk without any drive letter specified, it will only check the drive that it's in. Try 'chkdsk C:\' and if that doesn't do much, try D:\, and then work your way through the alphabet. Also, you may need some more options. A bit dated, but have a look at this:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

I think you'll need 'chkdsk C:\ /f /r', but it's been a long time since I needed to do any Windows command line stuff. And long may that continue! :p

> **nickhopkins07 said:**
> I guess something that might help shed some light is if the blue screen that appears briefly, stayed on the screen longer so I could read what it was telling me. Do you think it would be recorded somewhere on the HDD? That I could maybe browse to via the Jaunty install.

Tbh, I don't know. You can certainly explore the Windows filesystem from Ubuntu but whether logs are kept in plain text (as they are in Linux) I'm not sure.
 
> **nickhopkins07 said:**
> I can't see why the Jaunty installation would have touched the partition Win 7 is o, and hence that Win 7 could be damaged in anyway.

Agreed. Since you used sda1 for Ubuntu I guess you didn't resize the Windows partition. Vista sometimes has a serious fit of the sulks if you resize it with the Ubuntu partitioner, and I guess that could happen with W7, but you didn't.

Oh, by the way, one other thing. You didn't make a swap partition. If you have plenty of memory that may not matter, but another thing to be aware of.

---

### Post by nickhopkins07 on 2010-04-02
If I run chkdsk c:\ I'm told "cannot open volume for direct access", which says to me, it knows there is something there, but cant open it.
 
I don't know if this is important, but when I'm in Jaunty, if I open up the volume Win 7 is on, I have to 'mount' it each time Jaunty has been restarted, I can't just double click it and the files are on view. If I go to the partitions properties and click on the volume tab, it is listed as having no Label and the mount point as /media/.
 
Feels like the win 7 partition isn't acting like a normal partition or something.

---

### Post by coffeecat on 2010-04-02
> **nickhopkins07 said:**
> I don't know if this is important, but when I'm in Jaunty, if I open up the volume Win 7 is on, I have to 'mount' it each time Jaunty has been restarted, I can't just double click it and the files are on view.

Not quite sure I follow you, but the normal thing is to go to the Places menu, single-click on the Windows partition, type in your password where prompted, and then a file browser will open. **Or**, Places > Computer > double-click on Windows partition icon, etc. If this isn't happening then perhaps something is wrong with the filesystem. How do you mean 'mount' it? From a terminal?

> **nickhopkins07 said:**
>  If I go to the partitions properties and click on the volume tab, it is listed as having no Label and the mount point as /media/.

Again, I don't follow you, but I'm posting from Karmic and there's been a few changes. Can you explain a bit more? No label is unimportant - I guess that means no partition label. The mount point won't be /media which is the main system folder in which mountpoints (sub-folders) are created. The mountpoint will be /media/*somethingorother*.
 
> **nickhopkins07 said:**
> Feels like the win 7 partition isn't acting like a normal partition or something.

I have one suggestion which *may* make things worse - or make no difference. In Jaunty, install the package ntfsprogs - that's a bundle of command line apps. Then try running...

```
sudo ntfsfix /dev/sda3
```From the ntfsfix manual.

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.If you want to read the whole lot, type 'man ntfsfix' in a terminal. What I'm hoping is that by scheduling a consistency check, it will force Windows to do a chkdsk on itself before you get to the blue screen. But do at your own risk.

Last thought - have you tried F8 as you attempt to boot into Windows? The first option - Repair your computer - might work where the recovery disc has failed. It will be worth trying before ntfsfix from Jaunty.

---

### Post by nickhopkins07 on 2010-04-05
Hey coffeecat, 
 
Thanks for the ideas again, I decided to put the whole thing down for a few days and enjoy the easter weekend!
 
I tried the NTFSFix idea, but it didn't seem to do anythign, on loading windows, it just blue screened again.
 
I did try using an XP disk to try running a Chkdsk, but it didn't like it, from looking on the net a bit more, seems like the NTFS structure might be damaged?

---

### Post by nickhopkins07 on 2010-04-06
Further more, I borrowed a Win 7 disk from work, just to see if the repair functions on that had more luck, which thye didn't. I did start the install process as well for interests sake, and slightly worryingly, the Win 7 installer found now drives on my laptop where it could actually install itself too, it found nothing at all.........

---

### Post by oldfred on 2010-04-06
I did not see a boot flag on your sda3 partition. Windows considers that the active partition and may not see it without the flag.

You can use gparted to set boot flag by right clicking on the partition and manage flags.

---

### Post by nickhopkins07 on 2010-04-06
Hey Oldfred,
 
Thanks for the tip, just gave that a go, but didn't seem to sort anything.

---

### Post by Mark Phelps on 2010-04-06
If this machine came with Win7 preinstalled, my guess is that the order of the partitions was as follows:
1) Recovery partition
2) Win7 Boot partition
3) Win7 OS partition

You can not boot Win7 from the second Win7 partition; you must boot it from the first.  So, you need to have your GRUB stanza booting Win7 from sda2, not from sda3.

Don't know why the Win7 Repair CD doesn't see anything -- but I've read posts about specially formatted "recovery partitions" confusing the recovery/repair MS programs so they can't see the remainder of the partitions on the drive -- which is why SOME OEMs put the recovery partition at the END of the drive, rather than at the beginning.

Because MS has made booting a lot more complicated in Vista/Win7 with the BCD instead of the old NTLDR and .ini files, you're pretty much stuck using their utilities to repair the boot loader.

If those don't work, and you're unable to clean restore the machine, you would need to contact the vendor to see if they will sell you full-image-restore media -- such that you don't have to rely on the recovery "partition" to restore your machine.

---

### Post by nickhopkins07 on 2010-04-06
Mark, thanks for the reply.
 
I'm guessing this is a non-starter of a question, but I'll show my ignorance once more and ask, can the position of the partitions be moved? I.e move the Windows partitions from SDA3 to sda2?
 
I'm guessing if I do end up doing a full win 7 re-install, I'm going to have to use Ubuntu to format the current windows partition, as the windowsa installer can't seem to see anywhere where it can install itself?
 
Thanks again guys.

---

### Post by oldfred on 2010-04-06
Mark Phelps is correct as the boot is sda2.  So the boot flag has to be on sda2 for windows to see the install. 

I missed the separate boot partition.

---

### Post by nickhopkins07 on 2010-04-06
Tried swapping the boot flag to sda2, but windows still blue screens on boot up.

---

