---
title: "GPL-partitioned, FAT32-formatted USB won't mount :-("
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2015-08-30
Hey guys!

I'm trying to create a UEFI-bootable Live USB for Ubuntu 15.04. I'm following [this guide]("http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media").

It says:

[LIST]
[*]You may still need to explicitly tell your computer to boot the media via UEFI.
[*]**A GPT partition table like in preinstallations of Windows 8 and later is recommended.**
[*]Use the latest AMD64 (LTS) ISOs, because these definitely contain UEFI bootloaders.
[/LIST]

So I created a GPT partition table, made a new partition and formatted it to FAT32 as [described here]("http://askubuntu.com/questions/509006/how-can-i-check-and-change-the-partition-table-type").

Now, when I plug in the USB key, Gparted sees it, but it won't mount!! [Here's a 14-second video of my problem]("https://www.youtube.com/watch?v=qNMDaKXz1Bs").

What am I doing wrong? Who among you has created a working UEFI-compatible Live USB, and how did you do it?

Thanks! - Matt

---

### Post by oldfred on 2015-08-30
Not authorized to see video,
Just post this:
sudo parted -l

But if creating a new Live installer, you normally do not have to partition in advance. It just is created by the tools you use to convert ISO to bootable drive, like unetbootin, rufus, and others.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by The Bright Side on 2015-08-30
Oops, my bad. Video is accessible now! My output:

thebrightside@SATANICDUCK:~$ sudo parted -l
[sudo] password for thebrightside: 
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4


Model: ATA WDC WD5002AALX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 2      1049kB  492GB  492GB   primary  ext4
 1      492GB   500GB  8190MB  primary  linux-swap(v1)


Model: ATA INTEL SSDSC2BP24 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  525MB  524MB   primary  ntfs         boot
 2      525MB   227GB  227GB   primary  ntfs
 3      227GB   240GB  12.6GB  primary  ext4


[I]Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdd: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  8004MB  8003MB  fat32              boot, esp[/I]

---

### Post by The Bright Side on 2015-08-30
I checked in Windows 10 and it recognized it, but said it wasn't formatted. I formatted (in Win10), then plugged back into Ubuntu. Same problem. I changed the partition table back to msdos using Gparted, created a new FAT32 partition and now it's accessible. Bit odd that Ubuntu doesn't recognize the GPL-partitioned drive, when the guide clearly says it's advised to make it GPL. :-/

---

### Post by The Bright Side on 2015-08-30
I copied over all the files from inside the 64-bit Ubuntu 15.04 installation ISO and for 3 files, I got an error message, saying the target file system does not support symbolic links. I skipped them.

Anybody experience this when making their own Live USB drives?

I feel pretty nooby now, and frankly a bit surprised that this happens. You'd think the guide is correct; it seems pretty popular...? I must be overlooking something. Any advice will be appreciated!

---

### Post by oldfred on 2015-08-30
I have only seen one post where a user said you could create an UEFI bootable flash drive just by extracting the ISO to a FAT formatted flash drive with boot flag. UEFI really only needs to find bootable files in the efi folder in the flash drive. But BIOS needs boot files and only installer configures that.

Normal way to install to flash drive is to use any of the tools used to create bootable flash drives. 
 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
      
 [URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL]
 [http://rufus.akeo.ie/](http://rufus.akeo.ie/)

I think one version did not create correct UEFI bootable flash drives, but forgot which it was. And some have issues with USB ports, or certain brands of flash drives. So if it does not work try a different installer or a different port or a different brand flash drive.


[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

### Post by The Bright Side on 2015-08-30
Thanks oldfred! It ended up working out, and I now have Windows 10 and Ubuntu 15.04 happily coexisting in UEFI harmony on my ROG laptop! :-)

---

