---
title: "Can not install dual boot 12.04 with WinXP"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by Sherman_Willden on 2014-04-29
I had Ubuntu 12.04 on before and removed 12.04. Now when I try to reinstall 12.04 dual-boot I get a message directly after the install and reboot. The message states something like ignore, skip mounting , m manual recovery. It will not boot into Ubuntu. Are there any workarounds for this? Did I just get a bad installation?

Thank you;

Sherman

---

### Post by Bashing-om on 2014-04-29
Sherman_Willden; Hi !

Chances are that grub did not install where your bios is expecting to "see" it, But, before (RE-)installing grub, show us what we are working with>
Post back - between code tags - the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and we can advise more directly.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Sherman_Willden on 2014-04-29
Thank you. Below is the output

sudo fdisk -lu
sudo unable to mkdir /var/lib/sudo/sherman: No such file or directory
[sudo] password for sherman:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 15601488 sectors
Units = sectors of 1 * 512 = 512 bytes
I/O Size ( logical/physical ): 512 bytes/512 bytes
Disk Identifier: 0xe122e122
Device Boot  Start  End  Blocks  System 
/dev/sda1 *   63    156280319  78140128+  HPFS/NTFS

sudo parted -l
sudo unable to mkdir /var/lib/sudo/sherman: No such file or directory
[sudo] password for sherman:
Model: ATA ST380021A
Disk /dev/sda: 80.0GB
Sector Size ( logical/physical ): 512 bytes/512 bytes
Partition Table: msdoc
Number     Start     End     Size     Type     File System     Flags
1              32.3kb   80.0KB 80.0KB  Primary  ntfs              boot

---

### Post by Bashing-om on 2014-04-29
Sherman_Willden; Well !

Both 'fdisk' and 'parted' only see Windows (NTFS) as installed onto that hard disk.

As cheap insurance, fire up the liveDVD once more to the desk top, and in the dash search box enter the term 'GParted' -> click on the resulting icon below the search box. GParted is ubuntu's partion editor, What does GParted see for partitions on device sda ? or for that matter nay other hard drives (physical) that are installed in the box.

If all that is on the hard disk is a NTFS partiton then, yeah a install of ubuntu is in order.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Sherman_Willden on 2014-05-01
I don't have a live DVD and I am using WInXP C:\ubuntu\ and C:\Documents and Settings\Sherman. It seems logical that only the Windows NTFS is mounted since Ubuntu is installed as a read-only disk which even root can not perform most functions. Should WinXP C:\ubuntu\disks\grub be empty? Is there a way I can modify the fstab file on the WinXP side? How do I get Ubuntu so it is mounted rw?

Thanks;

---

### Post by Bashing-om on 2014-05-01
Sherman_Willden; Wheleeel.

All I can surmise is that you have a WUBI install - ubuntu installed virtually inside of Windows. Not a dual boot installation at all.

I have no experience with WUBI, thus not able to help.

To aid those who have the experience; please post the output of terminal command:
```

mount

```

[INDENT]others will respond
[/INDENT]

---

### Post by fantab on 2014-05-02
The following Wiki should get you started, meanwhile:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

