---
title: "UEFI: Interesting simple method to boot - but how does it work?"
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by sudodus on 2015-10-15
> **oldfred said:**
> Actually if you want an UEFI only boot flash drive you do not need an installer at all.

You just need to format flash drive with FAT32 and set boot flag on. Then use whatever is your favorite extraction tool like 7zip to extract & copy ISO to FAT32 partition. UEFI boots from a FAT32 partition with a very long GUID (if gpt) to identify it. Gparted and some other tools use boot flag to set that GUID. A few UEFI want flash drive as gpt, most will boot with MBR as even MBR has a code for ESP - efi system partition.

Ubuntu has built in /EFI/Boot/bootx64.efi which really is a copy of grub, for booting in UEFI mode.

Normal installers do the format, extract, but also then install a BIOS boot loader. Ubuntu uses syslinux as BIOS boot loader but with UEFI only you do not need that.

...

I think I did what you described. Extracted with ***file-roller*** from **lubuntu-14.04.3-desktop-i386.iso**.

In my Toshiba in UEFI mode it does not work: "No bootable device -- Please restart system"

In other words, it finds nothing to boot from.

There is no hard-disk with an UEFI system in it. Would that be required?

I would guess that there must be a bootloader, but I wanted to try your method, because it is so simple :-)

This is the computer where I have tested systems made by mkusb during the development, so I know pretty well how to boot from it in UEFI mode as well as in BIOS mode.

Please advice how to use your simple method :-)

---

### Post by oldfred on 2015-10-15
I do not think 32 bit version is normally UEFI enabled. 
They have added a 32 bit UEFI for some of the light weight systems, but do not know details.

Using 64 bit Ubuntu.
If flash drive has FAT32 with boot flag and the /EFI/Boot/bootx64.efi then you should be able to boot from UEFI boot menu. A few UEFI seem to what flash drive as gpt, but most work with just MBR(msdos).

Have you tried with the 64 bit version?

---

### Post by ubfan1 on 2015-10-15
The default bootloaders have the architecture in their names, e.g. boot{arch}.efi, so for the x64 architecture (64 bit), the name is bootx64.efi, and that is what is supplied on the install media.

---

### Post by sudodus on 2015-10-15
My bad. Of course, I should have used an amd64 iso file. (I forgot that the architecture makes a difference because persistent live drives made with mkusb work in UEFI mode also when made from i386 iso files. But in that case a bootloader and EFI files are provided by the installer.)

I'm trying again with a clean MSDOS partition table and a FAT32 file system.

```
file-roller lubuntu-14.04.3-desktop-amd64.iso
```

I mark and paste from file-roller to a nautilus window /media/OLDFRED (in the pendrive). I want to test 'the GUI way'.

```
$ sudo parted -s /dev/sdd print
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdd: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4005MB  4003MB  primary  fat32        boot

$ 
```

It works :-) Lubuntu 64-bit boots and works like it should.

I'll try with a GUID partition table too (and a FAT32 file system).

```
$ sudo parted -s /dev/sdd print
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdd: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4003MB  4002MB  fat32              [COLOR="#FF0000"]msftdata[/COLOR]


```
I marked and pasted from file-roller, and after that changed from msftdata to a boot flag
```

sudo parted -s /dev/sdd print
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdd: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4003MB  4002MB  fat32              [COLOR="#0000FF"]boot[/COLOR]

$ 
```

It works :-) Lubuntu 64-bit boots also with a GUID partition table, GPT.

This is really a simple method, particularly with an MSDOS partition table and a FAT32 file system.

---

### Post by oldfred on 2017-09-19
Main install guide:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode     
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)

---

### Post by C.S.Cameron on 2017-09-19
This method of making a boot drive also works in Windows using 7zip.
Casper-rw files work for persistence but when I create a casper-rw partition, UEFI no longer sees the drive.

---

### Post by sudodus on 2017-09-19
> **C.S.Cameron said:**
> This method of making a boot drive also works in Windows using 7zip.
Casper-rw files work for persistence but when I create a casper-rw partition, UEFI no longer sees the drive.

Yes, that's right.

I have mixed that into the instructions without stating those things clearly

1. Do you think it is better to make separate sets of instructions for Windows?

1.1 Running in Windows
1.2 Creating a Windows install drive

2. I tested (again) and noticed that persistence with a partition fails, also when in another drive. But that works from a cloned drive. ***Do you understand why?***

- Could it be that the links cannot be copied into the FAT32 system?

- Or that the permissions of some files cannot be preserved?

- Or could there be some logical statement, that decides what to do depending on the file system?

Both a cloned system and mkusb's persistent live system use a cloned copy of the iso file and preserve the ISO 9660 file system.

3. If you have the time, please test the instructions and tell me what is wrong or unclear (and how it should be improved) :-P

---

### Post by ubfan1 on 2017-09-19
The link "ubuntu" cannot be replicated on a FAT filesystem, so that is left out of the copy (from ISO9660 to FAT).  The grub.cfg kernel boot line references the link (some preseed reference), so that is a problem.  Remove the part with the link, and replace it with live-media-path=/casper/ ignore_uuid  and that now boots 16.04.  Adding the word persistent for a persistent partition now fails on 16.04 -- at some earlier release, I think it was working.  The failure dumps the boot into initramfs.

---

### Post by sudodus on 2017-09-20
> **ubfan1 said:**
> The link "ubuntu" cannot be replicated on a FAT filesystem, so that is left out of the copy (from ISO9660 to FAT).  The grub.cfg kernel boot line references the link (some preseed reference), so that is a problem.  Remove the part with the link, and replace it with live-media-path=/casper/ ignore_uuid  and that now boots 16.04.  Adding the word persistent for a persistent partition now fails on 16.04 -- at some earlier release, I think it was working.  The failure dumps the boot into initramfs.

Thanks :-)

This is a simple method, and it is good to understand what works, what does not work, and why.

I intend to look into alternatives with UDF, Universal Disk Format.

Anyway, mkusb provides persistence with partitions.

---

### Post by sudodus on 2017-09-20
This simple method works with a UDF file system and a casper-rw partition :-) but only in BIOS mode.

```
sudo mkudffs -b 512 --media-type=hd --lvid=did-it-myself /dev/sdd1
```

See the attached screenshot.

The system made this way refused to boot in UEFI mode :-( I tried to convince it with a boot flag and an esp flag, but I think the UEFI-BIOS systems want a FAT32 file system in order to accept booting via USB in UEFI mode (and then persistence is limited to a casper-rw file). I tried in three computers (Lenovo and Toshiba laptops and an Intel NUC).

---

### Post by C.S.Cameron on 2017-09-20
I set up the UEFI drive with a casper-rw file and "persistent" added to grub.cfg.
UEFI drive uses casper-rw file OK.
I plug in mkusb type drive with casper-rw and home-rw partitions, then boot UEFI drive.
UEFI drive now uses the persistent partitions from the mkusb drive.
I make new drive with casper-rw and home-rw partitions only.
UEFI drive goes back to using the casper-rw file.
Removing the casper-rw file but not word "persistent" goes BusyBox.

---

### Post by sudodus on 2017-09-20
Confusing :-)

It is not easy to understand how the casper-rw files and partitions are selected, and when they are possible to use, particularly not when there are more than one.

---

### Post by C.S.Cameron on 2017-09-20
Oops, on further examination I found the UEFI drive was actually using the internal casper-rw file, (for program installs etc), and the mkusb drive home-rw partition, (for downloads, documents and desktop items). 

It seems an internal casper-rw file is required for persistence?

---

