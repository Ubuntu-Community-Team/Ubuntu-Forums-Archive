---
title: "GRUB headaches when installing Ubuntu 7.1 driving me to insanity."
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by allyak on 2008-03-18
Hi there,

I'm having issues trying to install Ubuntu 7.1 (Gutsy) from the Live CD. Ubuntu seems to install fine, but GRUB refuses to install.

The Ubuntu installer fails at 94% when it tries to install GRUB using the command: grub-install '(hd0)'

I ran the GRUB installer manually, using the command sudo grub-install '(hd0)' and I got the error message:

[FONT="Courier New"]Could not find device for /boot: Not found or not a block device.
[/FONT]

My machine (an ASUS A6Ja notebook) has a single 100 GB SATA drive with Windows XP already installed. The machine has a recovery partition, the main partition (with Windows XP installed) and I've now added two new partitions for Ubuntu: an ext3 partition for the OS and a 2 GB swap partition.

[FONT="Courier New"]Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6103cd94

Device Boot Start End Blocks Id System
/dev/sda1 1 243 1951866 1b Hidden W95 FAT32
/dev/sda2 * 244 11343 89160750 7 HPFS/NTFS
/dev/sda3 11344 12161 6570585 f W95 Ext'd (LBA)
/dev/sda5 11344 11915 4594558+ 7 HPFS/NTFS
/dev/sda6 11916 12161 1975963+ 82 Linux swap / Solaris[/FONT]

I'm trying to get GRUB installed so that the I can dual boot Win XP and Ubuntu, with priority to Win XP (I'm just testing the waters with Ubuntu for now).

Can anybody help out or tell me what's going wrong?

Thanks

Ally

---

### Post by ajmorris on 2008-03-18
hi,
on whatever you were using when you ran grub-install, could you please do the following:

```
1) sudo grub
```
```
2) find /boot/grub/stage1    *With this command, it should tell you what partition grub is installed to, however* if grub is not installed, it may find nothing. if this finds a partition, it will be (hd#,#)
```
```
3) root (hd#,#)  *Where #,# are the numbers from step 2*
```
```
4) setup (hd0)
```
```
5) quit
```
```
6) reboot
```

---

### Post by allyak on 2008-03-18
Thanks for your quick reply. I get this error after your second step:

[FONT="Courier New"]grub> find /boot/grub/stage1  

Error 15: File not found
[/FONT] 

What should I do?

---

### Post by HoTseChu on 2008-03-18
I found the same problems with my laptop, because of the recovery partition and the fact that sometimes XP and factory installations uses the MBR of the hard drive to boot. 

To solve this, other way is to start linux from Windows:

1) Install Linux and Grub on the linux partition only (not in the MBR).
2) Restart with a Gparted CD and flag linux partition as "boot". 
3) Restart, and now you can only boot in linux. Don´t worry if your XP seems to have dissappear.
4) In a console,as root, use the command: 

dd if=/dev/sda4 of=bootgrub.bin bs=512 count=1

Replacing "sda4" with your linux partition

5) Copy in a pen drive the file "bootgrub.bin"
6) Restart with Gparted CD and flag again Windows partition as "boot". Restart again and now only XP appears.
7) copy "bootgrub.bin" to c:/
8 ) Edit "c:/boot.ini" (is a system file and "read only", change permissions and windows options first) and write:
"c:\bootgrub.bin="Ubuntu 7.10 GNU/Linux" at the end  of the file.

Restart Windows and you will see the new option to boot.

Remember to clean from linux grub the Windows option to boot, don't work now.

Excuse me for my bad english. You can find an spanish and more complete version for a Lenovo T61 in: 
[http://www.ubuntu-es.org/index.php?q=node/72349](http://www.ubuntu-es.org/index.php?q=node/72349)
I wrote it from two post in english about the same thing, but I couldn't find them now. Sorry.

Good luck.

---

### Post by allyak on 2008-03-24
Thanks for your post, but I don't feel comfortable messing around so much with the boot up sequence of my computer.

I'm tech-savvy, but not tech-savvy enough to try and recover my computer if things go wrong with the booting--all that fiddling with GRUB, menu.lst files, etc. etc.

Was hoping to just test the waters with Ubuntu. Looks like that won't be happening now.

Thanks again for your help.

If anybody has an easier alternative, I'd love to know and finally check out what all the Ubuntu fuss is about.

Cheers,

Ally

---

### Post by logos34 on 2008-03-24
> **allyak said:**
> 
Device Boot Start End Blocks Id System
/dev/sda1 1 243 1951866 1b Hidden W95 FAT32
/dev/sda2 * 244 11343 89160750 7 HPFS/NTFS
/dev/sda3 11344 12161 6570585 f W95 Ext'd (LBA)
**/dev/sda5 11344 11915 4594558+ [COLOR="Red"]7 HPFS/NTFS[/COLOR]**
/dev/sda6 11916 12161 1975963+ 82 Linux swap / Solaris[/FONT]

If sda5 is supposed to be your ext3 root, no wonder you're having problems.  It's formatted ntfs (either that or fdisk is wrong).

Try installation again but make sure to specify correct filesystem type for /.  

If grub still refuses to install to the mbr, you can always send it to a floppy*.  At least that way windows will remain bootable not matter what happens to grub and/or linux.

*step 7 'Ready to install' screen>press 'Advanced' button>change to **(fd0)**

---

### Post by allyak on 2008-03-25
Thanks for your reply Logos34.

I'm fairly sure fdisk is wrong. When installing Ubuntu, I *had* set /dev/sda5 to be ext3, and /dev/sda6 to be set to swap using the installers partition manager.

GParted correctly shows the /dev/sda5 to be formatted as ext3, and /dev/sda6 to be formatted as swap. fdisk seems to get it wrong.

Thanks as well for your floppy disk suggestion, but my laptop doesn't have a floppy drive.

Ally

---

### Post by logos34 on 2008-03-26
> **allyak said:**
> Thanks for your reply Logos34.

I'm fairly sure fdisk is wrong. When installing Ubuntu, I *had* set /dev/sda5 to be ext3, and /dev/sda6 to be set to swap using the installers partition manager.

GParted correctly shows the /dev/sda5 to be formatted as ext3, and /dev/sda6 to be formatted as swap. fdisk seems to get it wrong.

Thanks as well for your floppy disk suggestion, but my laptop doesn't have a floppy drive.

Then use the method described above by Hotsechu--write grub to the linux /, and use windows bootloader to chainload grub.

sudo grub
> root (hd0,4)
> setup (hd0,4)
> quit

dd if=/dev/sda**5** of=bootgrub.bin bs=512 count=1

copy the .bin file to windows C: drive, add entry to boot.ini.

OR use [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html")

---

