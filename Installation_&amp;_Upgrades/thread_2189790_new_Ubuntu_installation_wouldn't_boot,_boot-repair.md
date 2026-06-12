---
title: "new Ubuntu installation wouldn't boot, boot-repair couldn't fix it"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by rclocher3 on 2013-11-24
Hi all,

So I got a new Fujitsu Esprimo E710 computer that had Windows 7 on it, and I decided to erase Windows and put Ubuntu on instead.  I hedged my bets first by booting a live CD and using partimage to copy the big NTFS partition to my own private rescue partition.  Then I ran gparted and deleted the big NTFS partition and created an ext4 partition and a linux-swap partition in its place, ignoring several small NTFS partitions that I assumed had something to do with the factory restore utility.  Then I installed the amd64 version of Ubuntu.

When I booted the computer it came up in a rescue mode, and it wanted to reinstall the factory rescue image.  I figured I had simply forgotten to set the boot flag on the ext4 partition, so I fired up gparted again and did that.  Then when I booted I got the dreaded black screen saying:

"PXE-E61: Media test failure, check cable
 PXE-M0F: Exiting Intel Boot Agent
 No bootable device - insert boot disk and press any key"

So next I ran boot-repair, and I clicked on that highly-seductive button that says "Recommended repair (repairs most frequent problems)".  It said something about the computer being set to boot in EFI mode, but there was no EFI partition, did I want to continue?  So I canceled out of that, and created a fat32 partition of about 200 MB at the start of the disk and made it bootable, and then I ran boot-repair again.  This time boot-repair did its work without complaining.  As part of the procedure boot-repair had me copy & paste several commands into a terminal, commands that looked like they were installing some special EFI version of GRUB.

Now when I try to boot I get a black screen with the message "This is not a bootable disk.  Please insert a bootable floppy and press any key to try again ..."  When I press any key, I'm back to the "PXE-E61: Media test failure, check cable" error.

The last time I ran boot-repair it gave me this URL: [http://paste.ubuntu.com/6467583/](http://paste.ubuntu.com/6467583/) 

 I looked in my BIOS, and I didn't see any choice to boot in legacy mode, so I think I'm pretty stuck.  I did see that "[ubuntu]" is the first choice in the boot device list.  Can anyone help me figure out how to make Ubuntu boot?  I suppose if nothing else I could copy my private rescue image off the computer and then try again with the Ubuntu installer, but have it wipe the entire hard disk first this time.
 
- Rob

---

### Post by Bucky Ball on 2013-11-24
> => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.

You're not booting from grub and probably need to install it to sda1.

> sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 2048.
    Operating System:  
    Boot files:        /EFI/ubuntu/grubx64.efi

Looks like you have the regular grub on sda9 and the EFI one on sda3. 

I know little about EFI, but I might suggest you install grub to sda1. I think that's where the sda3 grub should be. You can do that using Boot Repair from the LiveCD. See here down the page a bit:

[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

You may then need to run boot repair again to put it all back together. If this gets your Ubuntu booting but not Windows, open a terminal and run:

```
sudo update-grub
```

Incidentally, in BIOS, there should be a 'EFI boot order' and a 'Legacy boot order' somewhere.

---

### Post by fantab on 2013-11-24
You have 'msdos' partition table on both your hard disks. EFI does NOT work with 'msdos' table. In other words, you don' have EFI/UEFI. It is strange that Boot-Repair misread the situation. Probably some setting in your BIOS must have triggered it.

Are you sure you don't have Windows on those HDDs?
IS your DATA SAFE? Where is it on your second HDD?
> [COLOR=#000000]parted -l:[/COLOR]
Model: ATA ST3500413AS [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
**Partition Table: msdos**

Number  Start   End     Size    Type      File system     Flags
3      1049kB  226MB   225MB   primary   fat32           boot
**1      228MB   2150MB  1922MB  primary   ntfs            diag **[COLOR=#ff0000]*#[this partition probably still has windows boot files]*[/COLOR]
2      2151MB  500GB   498GB   extended                  lba
9      3630MB  413GB   409GB   logical   ext4
10      413GB   434GB   21.0GB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
8      434GB   486GB   51.7GB  logical   ext2
5      486GB   490GB   4718MB  logical   ntfs            diag
6      490GB   495GB   5150MB  logical   ntfs            diag
7      495GB   500GB   4679MB  logical   ntfs            diag


Model: WD My Passport 0730 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
**Partition Table: msdos**

Number  Start   End    Size   Type     File system  Flags [COLOR=#000000]1      1049kB  500GB  500GB  primary  ntfs[/COLOR]

Edit: I don't think that the 'factory restore' will work without windows. Confirm this. If it won't then there is no point in having those additional partitions around.
Try factory restore to see if it works...

---

### Post by rclocher3 on 2013-11-25
Thanks very much for your time, Bucky and fantab, I really appreciate it!

After a night's sleep I saw things a bit differently.  I saw that I could heroically try to patch my installation so that it could boot, or I could just admit that I made a silly mistake and start over.  Patching my installation would have meant learning quite a lot about partitions, boot tables, UEFI, and so on; with all due respect to those people who work on such things for a living, I'm just trying to get my own machine going and I'd rather not spend hours on those things.

So what I did was to copy my own private backup image off the computer (to the USB-connected hard disk /dev/sdb), and then use the factory restore disks to restore the hard disk to the way it was when it left the factory.  Then I installed Ubuntu and told the installer to erase the hard disk.

 Here's the important thing that I learned: booting an operating system has become a much more complicated process, because there is "legacy" booting the BIOS way, and now also the UEFI way.  UEFI is more demanding and finicky, especially if Secure Boot is involved.  The way that the Ubuntu installer figures out how to make Ubuntu bootable is to see how an existing OS boots, and then copy that method.  So if you are installing Ubuntu onto a computer that has a different OS installed, let the Ubuntu installer see the other OS.  Don't damage a Windows installation for the fun of it by deleting its NTFS partition with gparted, and then expect Ubuntu to be installed so that it boots correctly.

- Rob

---

### Post by Bucky Ball on 2013-11-25
Sounds like you're up and running. If your problem is solved, please mark the thread as solved by following the instructions in my signature. Thanks.

Now you're going to come in handy when someone else gets into the same pickle. ;)

---

