---
title: "Ubuntu USB Installer v0.2 + Ubuntu 9.10"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by alfaalex101 on 2009-12-20
I have a 4 GB FAT32 flash drive and I'm installing Ubuntu on it with USB Installer v0.2 yet I need my files to stay on there -  the install says:

```
The contents of this drive **may **be deleted and the MBR overwritten! Make sure this is not your Windows Drive!
```

Will it delete my stuff? (I'm installing it without persistence with more than 700mb of space to spare on my 4GB flash drive)

---

### Post by phillw on 2009-12-20
> **alfaalex101 said:**
> I have a 4 GB FAT32 flash drive and I'm installing Ubuntu on it with USB Installer v0.2 yet I need my files to stay on there -  the install says:

```
The contents of this drive **may **be deleted and the MBR overwritten! Make sure this is not your Windows Drive!
```Will it delete my stuff? (I'm installing it without persistence with more than 700mb of space to spare on my 4GB flash drive)

Hi, when doing things like putting a boot system onto anything (hard drive / usb drive / memory stick) There is a golden rule ....

BACK IT UP

If you follow that rule, you will find that Murphy's Law tends to leave you alone and goes looking for an easier target.

As it will be putting data into a specific area of your usb stick, it is possible that it will over-write existing data. Not deffinate, just possible - hence the warning.

Regards,

Phill.

---

### Post by efflandt on 2009-12-20
The ISO info it extracts and copies onto the USB is only about 700 MB (the size of a CD), so even if you did make a 1 GB persistent file, it should not step on your existing file(s) as long as you do NOT hit the "Format" button.  Although, you should certainly have copies of your files somewhere else just in case.

Make sure that you select the partition (1) and not the drive (with no number) and that none of your existing files have the same name as directories or files in the root of the USB.

Following is an example (although this is Mint-8 based on Ubuntu 9.10), but note that my persistent file (casper-rw) is 3 GB, so for example if yours was 1 GB, you would still have 2 GB vfat space remaining that Windows could access, or without any persistence you would still have 3 GB free.

```
efflandt@efflandt64-desktop:/media/B69A-DC69$ df .
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdf1              3905516   3829624     75892  99% /media/B69A-DC69
efflandt@efflandt64-desktop:/media/B69A-DC69$ ls -l
total 3125292
drwx------ 2 efflandt efflandt       4096 2009-12-19 04:15 casper
-rwxr-xr-x 1 efflandt efflandt 3200253952 2009-12-19 04:24 casper-rw
drwx------ 3 efflandt efflandt       4096 2009-12-19 04:15 dists
-r-xr-xr-x 1 efflandt efflandt      14607 2009-12-19 10:14 ldlinux.sys
-rwxr-xr-x 1 efflandt efflandt       3541 2009-12-19 10:14 md5sum.txt
drwx------ 4 efflandt efflandt       4096 2009-12-19 04:15 pool
drwx------ 2 efflandt efflandt       4096 2009-12-19 04:15 preseed
-rwxr-xr-x 1 efflandt efflandt        222 2009-12-19 10:14 README.diskdefines
drwx------ 2 efflandt efflandt       4096 2009-12-19 04:15 syslinux

```

---

