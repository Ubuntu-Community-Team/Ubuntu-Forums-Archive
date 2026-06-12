---
title: "FAT32 Live USB Question"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by kbrafford on 2010-09-04
I have a ginormous 32GB "Patriot" USB keychain drive, and I have done the following to it:

1) Formatted it FAT32 in Windows
2) Used the Universal-USB-Installer-1.7.9.1 to create a persistent Live USB (with 4GB Persistence casper-rw file), without reformatting, so it's still FAT32

That works really well, and I have a flash drive with 22GB of free space on it.

Next,

3) I created a directory off of the root called zDATA ("z" so it shows up at the bottom)

That is how I add/remove data to/from the drive from Windows

Question:

How can I mount the stick in Ubuntu so I can also access the zDATA directory?

Thanks for your help!

--Keith Brafford

---

### Post by C.S.Cameron on 2010-09-04
Any data that you put to it from windows can be found in "cdrom" when you are booting from the USB drive.

ie look in cdrom/zDATA

---

### Post by kbrafford on 2010-09-04
> **C.S.Cameron said:**
> Any data that you put to it from windows can be found in "cdrom" when you are booting from the USB drive.

ie look in cdrom/zDATA


Looks like it's capital Z:
[FONT=Courier New][SIZE=1]
ubuntu@ubuntu:~$ ls /cdrom
ls: cannot access /cdrom/ZDATA: Input/output error
autorun.inf  install      pool                ubuntu                         ZDATA
casper       ldlinux.sys  preseed             Uni-USB-Installer-Copying.txt
casper-rw    md5sum.txt   README.diskdefines  Uni-USB-Installer-Readme.txt
dists        pics         syslinux            wubi.exe
ubuntu@ubuntu:~$ ls /cdrom/ZDATA
ls: cannot access /cdrom/ZDATA: Input/output error
ubuntu@ubuntu:~$ [/SIZE][/FONT]

But still is not usable by me.

Is there no way to make this drive accessible by me?

--Keith Brafford

---

### Post by C.S.Cameron on 2010-09-05
If you put stuff in /cdrom while booting the pendrive can you access it from windows?

Open the thumb drive in nautilus do you see ZDATA?

---

### Post by kbrafford on 2010-09-05
> **C.S.Cameron said:**
> If you put stuff in /cdrom while booting the pendrive can you access it from windows?

Open the thumb drive in nautilus do you see ZDATA?

No, nothing I do lets me see /cdrom/*

And I *can't* open the thumb drive in nautilus.  It doesn't show up as its own thing at all.

---

### Post by C.S.Cameron on 2010-09-05
How about, start nautilus, click filesystem, then click cdrom.

---

### Post by kgas on 2010-09-05
pl give the output of fdisk -l

---

### Post by kbrafford on 2010-09-05
> **C.S.Cameron said:**
> How about, start nautilus, click filesystem, then click cdrom.

Ah, that works.  I can see my ZDATA directory and read its files, but I can't write to it.  Is there any way to change that?

---

### Post by kbrafford on 2010-09-05
> **kgas said:**
> pl give the output of fdisk -l
[FONT=Courier New]
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde3973a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14793   111835048+   7  HPFS/NTFS
/dev/sda2           14794       64601   376548480    5  Extended
/dev/sda5           14794       64601   376548448+   7  HPFS/NTFS

Disk /dev/sdb: 32.0 GB, 32010928128 bytes
255 heads, 63 sectors/track, 3891 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d930a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3892    31260640    c  W95 FAT32 (LBA)[/FONT]

---

### Post by C.S.Cameron on 2010-09-05
> **kbrafford said:**
> Ah, that works.  I can see my ZDATA directory and read its files, but I can't write to it.  Is there any way to change that?

Try creating a directory named maybe XDATA in the cdrom directory while booted from the flash drive.
It may not want to modify a folder created with Windows for some reason.

---

### Post by kbrafford on 2010-09-05
> **C.S.Cameron said:**
> Try creating a directory named maybe XDATA in the cdrom directory while booted from the flash drive.
It may not want to modify a folder created with Windows for some reason.

Creating folders is grayed out.  It's a read only resource.

---

### Post by C.S.Cameron on 2010-09-05
Hmm, This seems to be something new with 10.04.
Even with "gksu nautilus" cdrom seems to be read only.

---

### Post by kbrafford on 2010-09-05
> **C.S.Cameron said:**
> Hmm, This seems to be something new with 10.04.
Even with "gksu nautilus" cdrom seems to be read only.

Cool...if it used to be writable, can I "undo" that change and make a writable directory that will let me use all 32GB of my stick?

---

### Post by oldfred on 2010-09-06
I do not understand why you have it mounted in cdrom which is a read only device. My USB flash drive is mounted in media.

fred@fred-LucidDT:~$ cd /media
fred@fred-LucidDT:/media$ ls
backup  C0CC-4E19  cdrive  floppy  floppy0  New Volume
fred@fred-LucidDT:/media$ cd 'New Volume'
fred@fred-LucidDT:/media/New Volume$ ls
boot_info_script055.sh  chrootbash.sh  ISO  lost+found
fred@fred-LucidDT:/media/New Volume$ cd ..
fred@fred-LucidDT:/media$ cd C0CC-$E19
bash: cd: C0CC-: No such file or directory
fred@fred-LucidDT:/media$ cd C0CC-4E19
fred@fred-LucidDT:/media/C0CC-4E19$ ;s
bash: syntax error near unexpected token `;'
fred@fred-LucidDT:/media/C0CC-4E19$ ls
boot               sources                           WinFixBoot.txt
bootmgr            Windows 7 64-bit Repair Disc.iso  winmbr.bin
EasyBCD 2.0.1.exe  Windows7-USB-DVD-tool.exe         wpa2.txt
fred@fred-LucidDT:/media/C0CC-4E19$ 

With a 32GB drive why not a full install just like a second drive and install as many ISOs as you want to boot for installing & repairing.

If you want to share part with windows just make the FAT32 partition first and put linux partitions after that one.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by kbrafford on 2010-09-06
> **oldfred said:**
> I do not understand why you have it mounted in cdrom which is a read only device.

Because I am new to live-CDs and ubuntu and I made my USB stick following these instructions:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

:-)

It looks like you have a setup that does what I want, and that I need to increase my level of sophistication pronto!

---

### Post by C.S.Cameron on 2010-09-06
I tried another persistent install using usb-creator.
This time gksu nautilus lets me read and write to a Windows folder in cdrom.
It may be easiest to create a FAT32 partition for storage like Fred mentioned. It needs to be the first partition for windows to see it.

Fred:
cdrom is where the stuff on the Live USB can be found while booted from the USB.

---

