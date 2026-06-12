---
title: "How to replace Grub2 with Syslinux on non-booting USB stick"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by WorBry on 2013-02-17
I am having a problem getting an installation of the 'Minimal' system to  boot from USB flash drive on my PC. It was installed from the "Minimal  CD' OSO using the Command Line procedure. 

The reasons why I have had to install the 'minimal' system first, rather  than the full Lubuntu 12.10 system, are chronicled in a rather  long-winded thread in the Newbie section. 

[http://ubuntuforums.org/showthread.php?p=12511990#post12511990](http://ubuntuforums.org/showthread.php?p=12511990#post12511990)

The dialogue from post#29 onwards summarizes the current state of play.

Basically, on booting from the USB stick I am presented with a blank  black screen (with flashing cursor at top left) that does not progress  to loading Grub. Pressing Shift adds the text GRUB, but still it does  not load.   

The same installation made on an external USB hard-drive boots perfectly  well. And when I tried installing to the same USB stick (16GB Lexar) on  another PC (Dell Dimension 3100 - all Intel components) it booted on  that PC without any problems. So it can't be a problem the USB stick  itself. 

So it would appear that the BIOS on my PC has a particular problem  handling the Grub2 boot instructions on a USB flash drive. This is a  fairly old (8 years) PC with MSI motherboard - PC details:

Motherboard: MSI (Via) KT4AV (IDE/PATA slots only, no PCI-E)
CPU: Athlon AMD XP2800+ (2.09GHz, 166MHz FSB)
RAM: 2 x 512MB DDR-400 (PC-3200) set to 166MHz bus.
GPU: nVidia GeForce FX5200 128MB (on AGP with 256MB aperture) 
HDD: 80GB WD Caviar IDE 
Currently running XP Pro SP3 (don't really want to run Linux as a dual-boot on the same HDD) 

I think on more modern PC's, USB flash drives are identified as USB-key devices. On this machine the BIOS recognizes  USB Flash Drives as USB-RMD-FDD, that is "a USB-interfaced ARMD device  that functions as a zip or 'floppy drive'", whereas the external USB  hard-drive (Lacie) is identified as a USB-HDD. I'm trying to understand  this more completely, but I think it has to do with the way BIOS is  directed to the boot sector on perceived 'ARMD devices'. As I  understand, in partitioned devices the first sector is the MBR defining  partitions, whereas in (normally) un-partitioned devices (like  floppies), the Boot Sector (Volume Boot Record VBR) is the first sector. Installing a  partitioned file system (like Linux) on a USB flash drive requires the  first sector to formatted in a FAT file format, making the first sector  the VBR which can then be recognized by the BIOS as a 'USB-RMD-FDD'  device. So basically BIOS is looking for a VBR and but GRUB is presenting MBR. I think that's what's happening? 

 
I have a notion that replacing Grub2 with the Syslinux bootloader might  be a solution. Why? Because when I was first trying out Lubuntu 12.10  from the 'Live' ISO installed on a USB stick it booted perfectly well,  and the application used to make that was the Pendrive Universal USB  Installer, which uses Syslinux as the bootloader. However, this only worked if I pre-formatted the USB stick to FAT format. If formatted to Fat32, it did not work. 

Since I have a working and bootable Lubuntu 12.10 system running on the  external USB hard-drive (with the necessary Syslinux tools installed) I  believe it must be possible to access the directories on the USB stick  that is not booting and replace or override Grub with Syslinux, or else  prepare the stick (possibly adding a Fat16 partition) that would allow  Syslinux to be installed after a fresh installation of the 'minimal'  system. 

I have come across articles that explain:

a) How to replace Grub2 with Syslinux (EXtlinux) as the boot-loader within the same working system:

 [http://shallowsky.com/linux/extlinux.html](http://shallowsky.com/linux/extlinux.html)

and

b) How to prepare a USB stick for booting a 'Live' ISO using Syslinux:

[https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html)

What I can not find is a procedure for replacing Grub2 with Syslinux on a  USB stick that already has the 'minimal' system installed but which  will not boot. 

Being a complete newbie, with (as yet) no experience in the use of  command line tools and only rudimentary understanding of linux  directories, I am at a loss as how to achieve this goal.

Or else is it possible to reconfigure Grub in some way to get it to work?

I could perhaps generate a Boot-Info report if it would help. I have at  least learned how to do that (with Grub Repair) within a working system,  but again I am unsure how to generate a report for the non-booting USB  stick when accessed from a booted system (on external USB hard-drive) or  the 'Live' CD.

---

### Post by WorBry on 2013-02-17
Just a thought - would I be better off using Lilo bootloader given this is an old PC? I see in the 'minimal' system command line installation there is an option to use Lilo instead of Grub2

---

### Post by oldfred on 2013-02-17
I only know some of grub2, but do not quite understand why a syslinux booted and grub did not.

All hard drives boot from MBR which is the first sector of a drive. And that sector has no format. The rest of the boot code is linked from the MBR to where ever on drive it has its code. Grub normally puts some data right after the MBR, syslinux, lilo & Windows have more boot code in the PBR or partition boot sector.

Some BIOS see flash drives as hard drives and others just list them as USB drives.
My desktop has many USB boot options, none of which boot my flash drive. But if selecting a hard drive then flash drive boots. But my laptop just shows a USB boot choice as one of hard drive, CD, USB or floppy.

If you just plug in flash drive and it is recognized, a run of BootInfo will try to scan it and show MBR and how grub is installed. But if it works on anther system, I would expect there not to be any issues.

---

### Post by C.S.Cameron on 2013-02-18
If your USB drive is booting fine on other computers then perhaps something like Plop will work on your machine.
You can add it to the hard drive or use a boot CD.

I have had computers that would boot USB HDD but not USB flash.
Plop will fix this.

The syslinux method sounds a little complex to me.

---

### Post by WorBry on 2013-02-18
Thanks, both of you. This is certainly an education for a newbie such as I. 

I've  probably run the 'minimal' system installation 4or 5 times over now,  trying different partition and/or file formats, without success. Current  installation has just 3. Don't have it mounted just now, but basically,  on this 16GB stick:

First partition: Ext4 Mounted: \Boot and flagged for boot. Size: 2GB 
Second partition: Ext4 Mounted: \   -  Size: the rest
Third partition: Swap Size: 2.2GB (2X RAM plus a little bit more) 

Which is probably the best configuration for trying front-end boot options, so I'll leave as is. 

Yes,  I think if there is a Syslinux solution, it is not a straightforward  one. Tried installing Syslinux on the stick (from 'Live' CD) but it told  me it needed \Boot in FAT format. So I tried setting up the partition  table (using GParted) with the Boot partition formatted FAT16 (and boot  flagged) and running the 'minimal' installation again, but it was  rejected at the partitioning/formatting stage 'not a valid format for  linux file systems....try ext2' or words to that effect. 

Learned  how to use Boot-Repair, and so tried replacing Grub2 with Legacy Grub,  but with the same result. I've yet to try Lilo. Looking at the command  line routine for manual installation, it would probably be easier to run  the 'minimal' installation again and choose Lilo instead of default  Grub2 at the final boot-loader stage. Just can't face doing another  installation right down.

One thing I did stumble upon, whilst  pursuing the 'Syslinux FAT Boot' issue is this tool makebootfat, which  apparently can be used to make USB-FDD devices appear to old-system  BIOS's (such as mine) as USB-HDD or vice-versa:

[http://advancemame.sourceforge.net/doc-makebootfat.html](http://advancemame.sourceforge.net/doc-makebootfat.html)

The key parameter is, quote:

> [SIZE=2]**-F, --mbrfat **[/SIZE][SIZE=2] Change the MBR image specified with the -m option to pretend to be a FAT filesystem starting from the first sector of the disk. This allows booting from USB-FDD (Floppy Disk Drive) also using a partition table generally required by USB-HDD (Hard Disk Drive). The MBR image specified with the -m option must have executable code positioned like a FAT boot sector. You can use the included `mbrfat.bin' file. [/SIZE]
If  this is the issue and this is a solution for it, I'm trying to figure  how. Is it something that could be applied to the stick as it is now -  'minimal' installation with Grub2, or is it something that would have to  be worked into an 'advanced' installation, which is beyond me?

Yes, I was wondering about Plop; I'll look at that also. 

Thanks. 
[SIZE=3]

[/SIZE]

---

### Post by WorBry on 2013-02-18
Here's the BootInfo on the USB stick ('minimal system' installation). Actually, did I put /home on a separate partition on this installation (done so many). This also was after replacing Grub2 with Grub Legacy and then putting Grub2 back (using Boot-Repair):

[http://paste.ubuntu.com/1677088/](http://paste.ubuntu.com/1677088/)

Obviously the USB stick is device sdc

Any clues there?

---

### Post by oldfred on 2013-02-18
I do not see anything in BootInfo script that looks out of place.

With my 16GB flash I just have two partitions. One is / (root) and the other data.

---

### Post by C.S.Cameron on 2013-02-18
I still think that if your flash drive boots on other computers, the problem is with your computer and not the install to flash drive.

---

### Post by WorBry on 2013-02-18
I agree entirely. It's a BIOS issue. 

Anyhow, went and found myself a refurbished (properly tested) 160GB IDE Hard drive for $20, about the same price as the 16GB USB stick.

Up and running and much faster than the USB External HDD that I tried before.  

I'll maybe re-visit the USB flash drive issue when I get more experienced, as it's useful to have. 

Thanks for your advice(s) :)

---

