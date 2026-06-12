---
title: "Filled external hard drive appears empty in nautilus after 12.10 reinstall"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Paco009 on 2013-03-25
I recently did a re-install of Ubuntu 12.10 on my computer backing up everything important onto a 1TB WD My Passport. Everything copied properly and the re-install worked fine. However now when I insert and mount my backup drive to retrieve my vital files, nautilus shows the drive as completely empty. Under the drive's properties it says 533.4 GB are used and 466.3 GB are free, but I cannot access my 533 GB of files...

The properties window also says the filesystem type is msdos, which might have something to do with it, but I'm not sure... I thought that I had formatted the drive as a Master Boot Record FAT drive/partition.

I booted into a live USB of Ubuntu 12.10 to see if I could access anything under that for some reason, but unsurprisingly, everything was exactly the same as previously described.

The drive in question was completely wiped and re-formatted in my previous installation of Ubuntu which is also the OS I used to copy all of my vital files afterwards.

Any help would be hugely appreciated. I'll happily provide any additional information needed, just let me know what's helpful. I absolutely HAVE to be able to recover the files on this drive, PLZ HELP.

---

### Post by Bashing-om on 2013-03-25
Paco009; Hi !

The fact that the file manager does not see the file system indeed does not bode well for a happy outcome. Nor formatting the drive as fat32; 

If this is a FAT32 filesystem, there is a 4GB limit on files being stored. You'll need to reformat to NTFS.
per ==> [URL="http://support.microsoft.com/default...b;en-us;314463"]http://support.microsoft.com/default...b;en-us;314463

[/URL]But, to address the issue at hand, one may look at what there is to work with/from; terminal commands from a liveCD:
```

sudo fdisk -lu
sudo parted -l 
sudo parted /dev/sda unit s print
```
Will give us a starting place.[INDENT=4]
try'n to help

[/INDENT]

---

### Post by darkod on 2013-03-25
msdos or Master Boot Record is type of the partition table. You can still have partitions with filesystem that is FAT32, ext4, etc. It's not very wise to keep using FAT32 these days, especially since ubuntu supports NTFS very good. So, if you need an ext disk to be readable by windows too, format it as NTFS. If you want it for ubuntu only, you can also do ntfs or you can go with ext4.

In any case, as suggested above, first post the:
sudo parted -l

and lets see what the output is.

---

### Post by dino99 on 2013-03-25
be sure to be logged as "user" not "root"

related question: [http://askubuntu.com/questions/97652/external-hdd-mounted-as-read-only-fat32](http://askubuntu.com/questions/97652/external-hdd-mounted-as-read-only-fat32)

---

### Post by Paco009 on 2013-03-25
rebeccca@Mariposa:~$ sudo fdisk -lu

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d8c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
/dev/sda5          501760  1465147391   732322816   83  Linux

Disk /dev/mapper/sda5_crypt: 749.9 GB, 749896466432 bytes
255 heads, 63 sectors/track, 91169 cylinders, total 1464641536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 743.6 GB, 743562018816 bytes
255 heads, 63 sectors/track, 90399 cylinders, total 1452269568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6333 MB, 6333399040 bytes
255 heads, 63 sectors/track, 769 cylinders, total 12369920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 6333 MB, 6333399040 bytes
255 heads, 63 sectors/track, 769 cylinders, total 12369920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba29eff

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

[B]Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb839[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953455804   976727871    c  W95 FAT32 (LBA)



rebeccca@Mariposa:~$ sudo parted -l
Model: ATA TOSHIBA MK7575GS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   750GB  750GB  extended
 5      257MB   750GB  750GB  logical


[B]Model: WD My Passport 07A8 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  fat32        lba
[/B]

Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 6333MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  6333MB  6333MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 744GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  744GB  744GB  ext4


Error: /dev/mapper/ubuntu-swap_1: unrecognised disk label                 

Error: /dev/mapper/sda5_crypt: unrecognised disk label                    




rebeccca@Mariposa:~$ sudo parted /dev/sda unit s print
Model: ATA TOSHIBA MK7575GS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End          Size         Type      File system  Flags
 1      2048s    499711s      497664s      primary   ext2         boot
 2      501758s  1465147391s  1464645634s  extended
 5      501760s  1465147391s  1464645632s  logical

---

### Post by darkod on 2013-03-25
Are you using encryption? You never mentioned that but according to the output it seems you do.

I haven't worked with encryption, is it possible that if you had encryption also on your old OS when you copied files to the ext hdd they were encrypted, and now the new OS has new encryption which doesn't match. So it shows there are 533GB used but not showing them to you.

You have to be really, really careful with encryption and know what you are doing. I don't, so I can't help much more.

---

### Post by Paco009 on 2013-03-25
The old 12.10 installation might have had an encrypted home folder setup as one of the options during the initial install, but that was it. The  external drive is brand new and was never encrypted. The new installation has an encrypted home folder and main drive all also created using the standard options available within the Ubuntu live install. As far as I know none of these should affect my ability to access the drive, but who knows.

It might also be helpful to mention that I'm unable to create any new files or folders within the drive using nautilus. Not sure if it thinks the drive's read only or that I don't have adequate permission or what...

---

### Post by oldfred on 2013-03-25
It looks like fdisk would not show the external but parted did show it.

Can you see it from Windows? As you have to use Windows to run chkdsk on Windows formatted partitions. Repairs to Windows formatted partitions have to be from Windows.

Again as stated before, chkdsk may not work or will take a lot longer on FAT32 as it does not have a journal and large file support like NTFS.

 Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by darkod on 2013-03-25
> **oldfred said:**
> It looks like fdisk would not show the external but parted did show it.

fdisk does show it Fred. It's in bold too. It shows the 1TB disk with a single FAT32 partition sdb1.

---

### Post by Bashing-om on 2013-03-25
Paco009;

I am in the same boat with darkod. - no experience or knowledge in respect to encrypted partitions. I am more than willing to assist in any manner, but, I am presently clueless how to proceed // I would think that until the partitions can be decrypted we are stuck.

[INDENT=4]'tween a rock and a hard place


[/INDENT]

---

### Post by darkod on 2013-03-25
In theory I agree that the ext disk wasn't encrypted itself. But if Home was encrypted and you copied files from there, are they decrypted and stored as plain files, or not? I have no idea.

Because if they are copied encrypted, you might be in big trouble. The point of ecryption is that you can hardly break it.

---

### Post by Paco009 on 2013-03-25
Just to clarify, as far as I know there should be no encryption relating to the drive in question. All the crypt/swap drives/partitions should be ones that were automatically created by Ubuntu during the install when I opted to encrypt the underlying install drive and to require a passphrase to decrypt the home folder. When the drive in question is mounted and nothing shows up on it, both of these encryption measures should be unlocked and thus irrelevant. I'm obviously at a loss too.... anything else I can try? I was planning on trying the drive on a Windows machine next just to see what happens...

---

### Post by Paco009 on 2013-03-25
My understanding was that after the home folder is decrypted all the files are accessible like normal. I've used encrypted home folders in the same way on other installations and copied files are always accessible on other drives/machines afterwards.

---

### Post by Paco009 on 2013-03-27
Tried the drive on a Windows machine today and it read everything fine, so definately not encrypted. Any ideas/suggestions as to how I can get it working on Ubuntu. The computer is a Toshiba Portege R935-P330 if that makes a difference. I would love to be able to restore my files.... help???

---

### Post by oldfred on 2013-03-27
Did you try chkdsk. 
Linux NTFS driver will not normally let you open NTFS partitions that need chkdsk, to prevent further damage. Even if Windows opens it.

---

### Post by steeldriver on 2013-03-27
Those 'My Passport' drives are funny - unless you reformatted the bare drive at some point, they initially appear as a 'Virtual CD' and have a little Windows (or Mac, depending on the version) client that manages the hardware level encryption. I'm not sure whether that really goes away even if you opt not to password-protect the actual data (using the SmartWare software).

[FWIW I'm fighting with one at the moment that appears to have died and won't mount past the 'CD Drive (E:)' stage even in Windows]

---

### Post by Paco009 on 2013-03-28
The drive in question is literally brand new. I took it out of the box, reformatted it to FAT32 to make it compatible with a PS3 and then copied all my files over to it no problem. After the 12.10 re-install the drive spins up and opens fine, but I cannot access anything or write to the disk. It is not encrypted, it is not corrupted. Other than that I have no idea what's going on. It's definitely something bigger than a faulty drive.

---

### Post by darkod on 2013-03-28
Can you open other usb disks or sticks in the same 12.10?

---

### Post by Paco009 on 2013-03-28
I have another Western Digital Passport formatted as NTFS which functions totally normal as well as a pair of flash drives which work fine (NTFS and ext4)

---

### Post by oldfred on 2013-03-28
Some have reported that some of these external drives do not come partitioned. If you just format and start using it is like a super floppy drive, not a partitioned hard drive. So then most systems have issues as they expect partitioning.

---

