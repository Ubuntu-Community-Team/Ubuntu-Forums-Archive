---
title: "Unable to dual boot into Ubuntu"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by MaeseFernando on 2008-05-26
Hi,

I'm trying to setup a dual boot XP/Ubuntu on my system, without much luck.

I have two HDs, sda and sdb. sda is used only for backups and sdb has windows XP installed on one partition.

I tried to install Ubuntu 8 workstation, and everything went fine (apparently) fine. Ubuntu was installed on sdb6 and a swap partition on sdb7.

When the system rebooted after finishing the installation, it went directly into XP and no grub menu shows up.

After [reading a post here]("http://ubuntuforums.org/showthread.php?t=80508"), I tried using [bootpart ]("http://www.winimage.com/bootpart.htm")to add sdb6 to the Windows boot menu.  I followed the same steps on that post but Linux still wont boot: I get a  message saying "Cannot load from harddisk."

I though it might be that grub was installed on sda instead of sdb6, so I copied the boot sector of sda with [bootpart ]("http://www.winimage.com/bootpart.htm")and tried again: it didn't work. When I select Ubuntu in the Windows boot menu, I go back to the Windows boot menu again (in a loop).

Now I'm completely lost. What am I doing wrong?  I can't be this difficult to have XP and Linux on the same machine...

---

### Post by MaeseFernando on 2008-05-26
BTW, this is the output of bootpart, if it helps:

[c:\bin\bootpart] bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com](http://www.winimage.com) and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 9254baca
 0 : C:* type=7  (HPFS/NTFS), size= 195358401 KB, Lba Pos=63
Physical number of disk 1 : e450e450
 1 : D:* type=7  (HPFS/NTFS), size= 113242153 KB, Lba Pos=63
 2 : D:  type=5  (Extended), size= 82116247 KB, Lba Pos=226484370
 3 : D:  type=7   (HPFS/NTFS), size= 10241406 KB, Lba Pos=226484433
 4 : D:  type=5   (Extended), size= 68902785 KB, Lba Pos=246967245
 5 : D:  type=83    (Linux native), size= 68902753 KB, Lba Pos=246967308
 6 : D:  type=5    (Extended), size= 2972025 KB, Lba Pos=384772815
 7 : D:  type=82     (Linux swap), size= 2971993 KB, Lba Pos=384772878
Physical number of disk 2 : 0
 8 : E:* type=6  (BIGDOS Fat16), size= 125296 KB, Lba Pos=32

---

### Post by conphuzed on 2008-05-26
try reinstalling grub to the mbr as follows:

sudo grub

grub> find /boot/grub/stage1 - this will provide a read out hd= hard drive, first number = hard drive number (as allocated by grub) second number = the partition on the hard drive

grub> root (hd?,?)

grub> setup (hd?)

grub> quit

NOTE: fill in the ? with the output from find /boot/grub/stage1

---

### Post by MaeseFernando on 2008-05-27
> **conphuzed said:**
> try reinstalling grub to the mbr as follows:


Will I still be able to boot into XP after that? 

Can I do this from a live CD? At this moment I can boot into linux.

---

### Post by zvacet on 2008-05-27
>  At this moment I can boot into linux.

Does it mean that you solved your problem?If not,and you can boot Ubuntu then

```
sudo fdisk -l
```

Post output here.

---

### Post by MaeseFernando on 2008-05-27
> **zvacet said:**
> Does it mean that you solved your problem?

No it was a typo. O:-) I can NOT boot into linux.

---

### Post by MaeseFernando on 2008-05-27
> **zvacet said:**
> Does it mean that you solved your problem?If not,and you can boot Ubuntu then

```
sudo fdisk -l
```

Post output here.

Here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9254baca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe450e450

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14098   113242153+   7  HPFS/NTFS
/dev/sdb2           14099       24321    82116247+   5  Extended
/dev/sdb5           14099       15373    10241406    7  HPFS/NTFS
/dev/sdb6           15374       23951    68902753+  83  Linux
/dev/sdb7           23952       24321     2971993+  82  Linux swap / Solaris

Disk /dev/sdc: 128 MB, 128450560 bytes
8 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         979      125296    6  FAT16


PS sdc is a usb drive.

---

### Post by zvacet on 2008-05-27
["]Reinstall grub.]("[URL="http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub"[/URL) If you have any questions after that post them here.

---

