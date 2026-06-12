---
title: "Understanding boot sectors and MBR"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by bugone on 2011-06-05
Hi,
I am attempting to setup a multiboot linux USB hard drive and I am a little confused as to how to setup the bootloader. This is more a learning experiment and I am trying to avoid GUI tools.
My understanding was that the MBR contained the boot code in the first 446 bytes and partition table and ID after that.
In my attempt I have partitioned the drive thus;
hda1 - 30mb ,Primary for bootloader files.
hda2 - 6GB Logical Ubuntu partition.
hda3 - 6GB Logical backtrack partition
hda4 - FAT32 Storage partition.
I have used logical partitions for the linux distros so I can have multiple installs once I figure things out.

The problem is booting to an extended partition. The automated tools I have used to create the isolinux installs seem to write boot code to the MBR and not to the first sector of the partition.
I have tried to boot the ubuntu install from a grub floppy but I get a 'boot error' from the following code

root (hd0,4)
chainloader +1
boot

I installed grub4dos with the windows XP ntldr/boot.ini method and once booted from grub4dos the command works fine. Why the difference?
I can install grub4dos into the MBR of my USB drive but if I use a tool to make another distro install it overwrites this and the drive becomes unbootable.
I can restore the MBR to bootable with the grub4dos tools but still can't boot into ubuntu, it returns a 'boot error' from grub. If I copy the bootsector from the MBR to the bootsector of the Ubuntu partition it messes up the partition table.
dd if=/dev/sdc of=/dev/sdc2 bs=446 count=1
How can I make the Ubuntu partition bootable? and why does copying the bootsector effect the partition table at all??
Cheers for any help. ](*,)

---

### Post by marcoftheknight on 2011-06-05
Sorry I can't help a little more I'm dealing with same type of issues. So far I have found these links which seem to be outdated but probably still educational. I figure since your doing a educational thing in this thread we should compile the best information. So here's my 2 links for managing multiple operating system which seem to give thorough explanation as to how an operating system is installed. This would be a good background information I think.

[http://ldp.linuxhelp.ca/HOWTO/pdf/MultiOS-HOWTO.pdf](http://ldp.linuxhelp.ca/HOWTO/pdf/MultiOS-HOWTO.pdf)
[http://www.pcmag.com/article2/0,2817,1730836,00.asp](http://www.pcmag.com/article2/0,2817,1730836,00.asp)
[http://www.linuxselfhelp.com/HOWTO/MultiOS-HOWTO-6.html](http://www.linuxselfhelp.com/HOWTO/MultiOS-HOWTO-6.html)

terminal code to pull up manual of a code in the terminal
Example what can I do with the mount command:~ man mount ( shows manual for the mount command)

If you find others let me know we should make a new PDF document one that's updated and focuses and sata, speed and what ever else you'd like to add.

Thanks

---

### Post by bugone on 2011-06-05
Thks marcoftheknight, this will make for some interesting reading. 
I have another problem now and I hope it wont spoil everything but I just tried to boot into the backtrack partition and it seems to be conflicting with the ubuntu partition and doesn't load properly. It loads to command line and when I start the x-server it loads the ubuntu desktop instead of the backtrack desktop and then freezes. hmmm
I'll have a read up on the links you posted and report back.
:?

---

### Post by oldfred on 2011-06-05
Did you install the boot files of both installs to the boot partition you created. You cannot do that without problems. I suggest no separate /boot folder unless you have an old system that cannot boot past 137GB, server, RAID or LVM configuration. Standard desktops do not need a separate /boot.

Grub2's boot loader does not like to be installed to a partition boot sector PBR. Old grub legacy's boot loader can be and windows uses the NTFS boot PBR to know whether to use ntldr for XP or bootmgr for Vista/7.

For an understanding of BIOS base booting with MBR partitioning see this. It is Vista but all BIOS/MBR system are similar as it is how they work. If you do not want all the detail at least review photos.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)


If you want to know the details of what you have installed where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by bugone on 2011-06-17
I understand now that the mbr and the pbr's are different in construction and pbr's are not interchangeable.
'Script info' is a pretty handy tool. I forgot to mention that I am trying to install the bootable syslinux images and not permanent installs to the hard drive. My main issues arise from how the particular syslinux (OS) is chosen for booting. Thus the boot partition and grub4dos install. If anyone has any info on how to set up a multiboot syslinux with persistance could you post some links or info.

---

### Post by oldfred on 2011-06-17
I have several Flash drives. One is a full install, another is a windows repair with additional ISOs of repairCDs, and a third is several ISOs, mostly versions of Ubuntu. I also boot ISO from grub2 on my hard drives, but do not use persistence. I think on flash drive only one install can have the persistence as otherwise it would conflict.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistent 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

---

### Post by bugone on 2011-06-21
Cheers for your help oldfred. After much reading I have decided to go down a slightly different path from the original plan and I am trying to build a compilation of distros onto a live_dvd and once this is working I will try to set this up on the usb and later try to incorporate persistance if it is possible. I have worked out how to compile a working dvd from a live_usb install but I am having trouble finding a list of the commands used in the isolinux.cfg files and how to edit certain files. Specificaly there is are commands used in the Ubuntu cd like "ui gfxboot bootlogo" which points to 2 config files and also "include menu.cfg" 
Any help is appreciated

---

### Post by oldfred on 2011-06-21
I prefer USBs now. I think all these scripts use grub2. You will have to translate the format, but they all show the various parameters used.

CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 
To setup multibooting:
multiboot055.sh
multicd.sh - combine Linux ISOS into one CD
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)


MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by bugone on 2011-06-28
Just a quick recap of what I've learned so far. In case anyone is reading this thread. Please correct me if I am wrong.
The mbr bootloader is contained in the first 440 bytes of the disk.
It could be erased while retaining the partition layout, uuid and disk label with the dd command thus;
dd if=/dev/zero of=/dev/? count=1 bs=440 (replace ? with your device)
The disk will still be accessible in an os but will not boot.
It doesn't seem to matter which os's bootloader is in the mbr as long as it points to the active partition.
(I haven't tested grub though). This sector could be robbed from any working hd with;
dd if=/dev/? of=file.name count=1 bs=440
and used on another disk successfuly
The bootsector on the partiton however is unique to each disk/partition layout/file location etc.. and points to the loader file location by sectors. It cannot be interchanged without damage to partition layout unless with a backup from the original. This would need to be recreated using os specicic tools.
e.g. the syslinux package includes an installer.
unmount the device and;
# syslinux -f -d /<location of syslinux.cfg> /dev/?
would restore the syslinux bootsector to the partition.
Hope this is of some use to someone. I will post more if I learn more.

---

### Post by YesWeCan on 2011-06-28
> **bugone said:**
> The mbr bootloader is contained in the first 440 bytes of the disk.
The first 446 bytes of sector 0. It's purpose is to identify an active partition (from the partition table) and execute its partition boot record (PBR) boot code.
> It could be erased while retaining the partition layout, uuid and disk label with the dd command thus;
dd if=/dev/zero of=/dev/? count=1 bs=440 (replace ? with your device)bs=446
> The disk will still be accessible in an os but will not boot.
An OS will be bootable if something else runs its PBR boot code. Or in the case of Ubuntu it runs Grub's core.img code.
> It doesn't seem to matter which os's bootloader is in the mbr as long as it points to the active partition.
This is not how it was designed to work. The MBR code should boot any partition. Only the PBR codes should be OS-specific.
> (I haven't tested grub though). This sector could be robbed from any working hd with;
dd if=/dev/? of=file.name count=1 bs=440
and used on another disk successfuly
Normally, you would copy the PBR code bs=446. Eg: you can copy the PBR code to a Windows partition and have Window's loader run it. This is how to add an OS to Windows boot menu.
> The bootsector on the partiton however is unique to each disk/partition layout/file location etc.. and points to the loader file location by sectors. It cannot be interchanged without damage to partition layout unless with a backup from the original. This would need to be recreated using os specicic tools.
Yes. The way the MBR-system is designed to work is that each OS has its own MBR bootable partition, by means of its own PBR boot code. This is how Windows works. It is simple and the primary partition that gets booted is the "active one" (boot flag set in MBR partition table).

Things get confusing with Ubuntu and Grub. Knowing no better, one might expect the Grub loader to be bootable via the PBR code in the Ubuntu partition. That would be nice and simple and MBR-compliant. Unfortunately, it is not designed to work reliably in this configuration. You can install it but it can break if the core.img file in /boot/grub gets moved and/or if the Ubuntu partition gets moved. This is why Ubuntu installs the Grub PBR code (plus core.img) to the MBR area at the front of the disk. The Grub PBR code only runs the Grub loader and ignores the partition table.

---

### Post by srs5694 on 2011-06-28
> **bugone said:**
> Just a quick recap of what I've learned so far. In case anyone is reading this thread. Please correct me if I am wrong.
The mbr bootloader is contained in the first 440 bytes of the disk.

Generally correct; however, some boot loaders don't quite fit in 440 bytes, and "bleed" into the next 6 bytes, which nominally hold the disk signature and two null bytes. I don't know offhand which boot loaders misbehave in this way.

> It could be erased while retaining the partition layout, uuid and disk label with the dd command thus;
dd if=/dev/zero of=/dev/? count=1 bs=440 (replace ? with your device)

Correct. I do *not* advise using 446 for this, as oldfred suggests, since some OSes (such as Windows) record and use the disk's serial number, and erasing 446 bytes rather than 440 will erase the serial number.

Incidentally, UUIDs are not stored in the MBR at all. MBR disks have a serial number, but it's not a UUID (which takes a very specific form). UUIDs are stored as part of Linux filesystems. In the GUID Partition Table (GPT) scheme, *G*UIDs (which are related to *U*UIDs) are stored as part of the partition table, but not in the MBR. GPT's GUIDs are different from a filesystem's UUIDs -- that is, the partition has a GUID and the filesystem has a UUID, and the two can be (and normally are) entirely unrelated values.

> It doesn't seem to matter which os's bootloader is in the mbr as long as it points to the active partition.

That depends on the boot loader. The DOS/Windows boot loader, and some others that work like it, point to and boot an active partition. Others, such as GRUB, use other methods to determine what OS to boot, so they don't work like that. Thus, when you install Linux (and hence GRUB to the MBR, if that's what the installer does), the MBR code doesn't look for an active partition any more. This can break things if you subsequently remove Linux, since you'll also be removing the configuration files upon which GRUB relies.

> This sector could be robbed from any working hd with;
dd if=/dev/? of=file.name count=1 bs=440
and used on another disk successfuly

I'd recommend backing up the whole thing (all 512 bytes) and then restoring only 440 bytes. That way, if you happen to have a boot loader that consumes 444 or 446 bytes, you'll be able to restore it. I do *not* recommend restoring that many bytes as a matter of course, though, since that will change the target disk's serial number. Of course, if you back up the whole MBR, you'll also have to be extra careful when restoring it to another disk (or to the same disk if you've changed its partitions), since restoring more than 446 bytes will end up overwriting some or all of the current partition table.

> The bootsector on the partiton however is unique to each disk/partition layout/file location etc.. and points to the loader file location by sectors. It cannot be interchanged without damage to partition layout unless with a backup from the original. This would need to be recreated using os specicic tools.

This varies depending on the boot loader in question. I don't happen to know the details for common boot loaders. It's actually possible to boot an OS that has no boot loader in its PBR. For instance, consider installing two Linux distributions, one of which provides GRUB (let's say it's Ubuntu) and the other of which you've told not to install a boot loader (let's say it's Gentoo). The Gentoo partition will then have no boot loader, but you can configure Ubuntu's GRUB to boot the Gentoo kernel, enabling you to boot Gentoo despite the fact that none of its partitions has any trace of boot loader code.

Note also that anything you learn about this topic will be inapplicable to computers that boot using the new EFI and UEFI systems. (UEFI is essentially EFI 2.x.) Under (U)EFI, the firmware is much "smarter." It can read a filesystem, and it reads boot loaders from its own partition, which is known as the EFI System Partition (ESP). (U)EFI doesn't rely on code stored in the MBR or in the PBR; OS-specific boot loaders are stored in the ESP, and they can use EFI services to load other files in the ESP, including configuration files, filesystem drivers, etc. Thus, almost everything can be managed using normal file operations rather than mucking with raw code. The one exception is setting the options for what boot loaders the (U)EFI itself knows about; that requires making (U)EFI system calls, which in Linux is done with a utility known as efibootmgr. Alternatively, you can configure this using the (U)EFI's own user interface. Either way, this information gets stored in NVRAM on the motherboard, rather than on the disk.

---

### Post by srs5694 on 2011-06-28
> **YesWeCan said:**
> The first 446 bytes of sector 0. It's purpose is to identify an active partition (from the partition table) and execute its partition boot record (PBR) boot code.

Since there's no official BIOS specification document, the "purpose" of the MBR boot code is ill-defined, beyond being code that's run by the BIOS when it first starts up. I suppose that's what we get for relying on multiple reverse-engineered implementations of a closed-source BIOS designed for a computer that IBM thought would have a very brief production lifespan. If the original BIOS designers have ever revealed the logic behind their implementations, I don't know about it. If you do, please provide a reference.

Those of you who are saying the boot code area is 446 bytes, please review the [Wikipedia article on MBR,](http://en.wikipedia.org/wiki/Master_Boot_Record) which clearly identifies the boot code area as being 440 bytes in size, with a parenthetical "(max 446)" to indicate that some boot loaders bleed over the allotted size into areas that have other interpretations.

---

### Post by YesWeCan on 2011-06-28
@srs5694: Are you Reed Solomon on amfetamines? :p
The way the MBR system works is perfectly clear to me. It is not ill-defined at all. I don't know what your beef is. Of course, IBM and Microsoft invented the MBR system so it is no surprise that Windows OS complies with it.
The Wiki article is one I have quoted in past posts. The code area can be up to 446. So if one is backing it up or restoring it one should use 446.

PS: Yes I know that Reed and Solomon are two separate people (before you correct me). ;)

---

### Post by srs5694 on 2011-06-28
There is no formal definition for the contents of the MBR. Hence, it's ill-defined, by definition. Consequences of ill-defined "standards" include issues like the uncertainty of the size of the code area -- 440 bytes vs. 446 bytes. Getting it wrong (either way!) is bad -- if you back up too little, the boot loader will stop working; if you back up too much, you trash data (namely the serial number) that some OSes use to identify disks. That's the main reason I recommended backing up the whole sector and restoring only as much as you need to restore. (Another is that you've then got a backup of the primary partition table, but that's another matter.) Better yet, restore the original code using whatever tools its authors provide for that purpose. In some cases, the code has to be customized for the system (such as GRUB's embedding the sector number of its secondary code in the MBR), so that's the best way to do it.

Just because you think something is "perfectly clear" doesn't mean that you're right. Unless you can provide documentation to back up your point of view, it remains just that -- *your* point of view. My "beef" is with assertions about the "purpose" of things that have no standards documents or other references that can be used to determine what the original intent was. Without such documentation, it's too easy to insert one's own biases into the matter.

---

### Post by YesWeCan on 2011-06-28
Zzzzz

---

### Post by ahears on 2011-06-28
If you don't mind, I'm coming in kind of late but I'm taking a step backward for a minute and going with your first post. **This may be a simple fix.** It looks to me as though you are attempting to use a Ubuntu 32 bit boot loader and a Backtrack Linux, and the two are not compatible. The boot loader for [COLOR=DarkRed]**_backtrack 4 is not compatible with the 32 bit Ubuntu loader and will not detect correctly from Ubuntu while residing in an extended partition._**[/COLOR] (I believe the old Backtrack 4 is still just a Linux install on a standard Fat partition table.) There is a line in the code of your '/boot/grub/grub.cfg' that needs to be modified manually, to get the grub to work for both OS types without halting or causing a Kernel Panic. The entries that look like this must be changed manually: 

> 
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
   [COLOR=Red] search --no-floppy --fs-uuid --set 400000ed0-c902-4234f-awe81-1ed33eb700081
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=400000ed0-c902-4234f-awe81-1ed33eb700081 ro   quiet splash[/COLOR]
    initrd    /boot/initrd.img-2.6.35-30-generic
}
There should be several, but the one that lists the backtrack partition on **/dev/sda3**. Backtrack 4 will not auto-configure the Magic Number (or UUID) from the Ubuntu 32 bit 'update-grub' or 'update-grub2' commands. [B]Here's how to fix it in the '/boot/grub/grub.cfg' from Ubuntu:
[/B] > 
'ls -l /dev/disk/by-uuid'
_Pay attention to the /dev/sda3 output_ as this will give you the magic number that Ubuntu will not give you automatically.  Compare the current grub.cfg UUID with the output from 'ls -l /dev/disk/by-uuid' to see if they are different.

**Then: add the UUID to the line in red:**

> 
search --no-floppy --fs-uuid --set [COLOR=Red]400000ed0-c902-4234f-awe81-1ed33eb700081[/COLOR]
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=[COLOR=Red]400000ed0-c902-4234f-awe81-1ed33eb700081[/COLOR] ro   quiet splash
**Where applicable, _they must match_.**

Do *_**not**_* run 'update-grub' after this, and reboot.

[B]Future Kernel updates to the system may change this and you might be forced to repeat the procedure after a system update. 

[/B]If you have installed Ubuntu after installing Backtrack your 'update-grub' command will not correctly determine the UUID for a Backtrack 4 partition. Get Backtrack 5 and you wont have to do this because the grub in Backtrack 5 is compatible with Ubuntu 32 bit and will correctly identify the UUID. Keep in mind that I wrote this under the assumption the you are installing grub from Ubuntu and are planning to multi boot several operating systems in multiple partitions on the same physical disk, while controlling your grub configuration from Ubuntu. I hope I'm not off of the topic.

---

### Post by bugone on 2011-07-10
ahears, I am using live images of the distro's. I am installing syslinux in the mbr and renaming the isolinux.cfg file/s to syslinux.cfg. I have setup a custom syslinux.cfg file in the first primary partition where I will chainload the logical partitions (one for each distro)
So it should boot from the first partition and then I am intending to chainload the logical partition for the distro I want to use with chain.c32
It is in this way I am hoping to later setup persistance for each distro. The main problem at the moment is getting syslinux installed properly in a logical partition. I cannot get it to boot from a logical partition at all. Even chainloading from grub. I install it with 
sudo syslinux -f -d /syslinux /dev/sdd5
and this completes without errors.
The print with boot info script of the partition is

sdd5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016
    Boot sector info:   Syslinux looks at sector 1411280 of /dev/sdd5 for its 
                       second stage. SYSLINUX is installed in the /isolinux 
                       directory. According to the info in the boot sector, 
                       sdd5 starts at sector 0. But according to the info 
                       from fdisk, sdd5 starts at sector 41945778.
    Operating System:  
    Boot files:
_______________________________________________________________________
as always any help is appreciated

---

