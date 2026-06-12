---
title: "installation choice"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by amigammon on 2010-02-12
I cannot find this problem with google or ubuntu forums. When I installed Ubuntu my intention was to install it on a separate partition, but when I used the CD that I created it gave me a choice that I can't exactly remember, but it allowed me to keep XP and install Ubuntu without using or creating another partition. So I can use both now, booting separately, of course. But where is Ubuntu?? I look around my HDD in windows and can't find it installed anywhere. If I boot up Ubuntu, it doesn't give me any clue as to where on my HDD it is located. My wish is to delete Ubuntu, offload my iTunes library from XP, and reinstall XP and sell this old Vaio. Then build a Medibuntu box for my living room.
But where is Ubuntu on my HDD??

---

### Post by raymondh on 2010-02-12
> **amigammon said:**
>  but when I used the CD that I created it gave me a choice that I can't exactly remember, but it allowed me to keep XP and install Ubuntu without using or creating another partition. ?

Does WUBI sound familiar?  Was/were you in windows when you loaded the ubuntu CD and installed ubuntu?  If so, you probably have a wubi-installed Ubuntu.  That means that ubuntu (the OS) is a file system within windows.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If not, and from Ubuntu, can you access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L, not 1 nor I.  Highlight the terminal output/results, right click to copy and paste it back in your next post.

Regards,

Raymond

---

### Post by amigammon on 2010-02-13
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1b2fdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         544     4369648+  12  Compaq diagnostics
/dev/sda2   *         545        5767    41953747+   7  HPFS/NTFS
/dev/sda3            5768       30401   197872605    5  Extended
/dev/sda5           11419       30401   152480916    7  HPFS/NTFS
/dev/sda6            5768       11181    43487892   83  Linux
/dev/sda7           11182       11418     1903671   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by raymondh on 2010-02-13
> **amigammon said:**
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1b2fdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         544     4369648+  12  Compaq diagnostics
/dev/sda2   *         545        5767    41953747+   7  HPFS/NTFS
/dev/sda3            5768       30401   197872605    5  Extended
/dev/sda5           11419       30401   152480916    7  HPFS/NTFS
[B]/dev/sda6            5768       11181    43487892   83  Linux
/dev/sda7           11182       11418     1903671   82  Linux swap[/B] / Solaris

Partition table entries are not in disk order

There it is.... your Ubuntu and its' corresponding SWAP.  sda6 and sda7 respectively.  They are both logical partition residing inside and EXTENDED partition.  The reason why it installed without "using or creating another partition" is because of the 4 partition limit.  4 Primary partitions or .... 3 primary + 1 extended (which can house as much LOGICAL partitions as able).  Now, a default ubuntu install will create 2 partitions (root and swap).  Since you already had 2 primary partitions (sda1 and sda2) and 1 extended (sda3).... the installer could not create more PRIMARY partitions hence installed Ubuntu as LOGICAL partitions within the EXTENDED.

Did I understand that you want to delete Ubuntu and restore the old VAIO to original configuration?  If so :

1.  Do you have the original XP install disc (not the recovery CD) which we would need to restore the MBR to a windows (XP) bootloader

2.  You would need a Ubuntu liveCD and use its' gparted program to delete the now, unwanted Ubuntu.  Better yet, download and burn a standalone [GPARTED CD]("http://gparted.sourceforge.net/download.php").  Choose the latest version.  We need to use that, or the liveCD, as it will unmount the partitions.  Some readings regarding deleting partitions using gparted

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

3.  Back-up/transfer all those files before proceeding.

Let us know if you need a quick how-to.

Raymond

---

### Post by amigammon on 2010-03-01
Thanks for the good, helpful info. Is it possible to see these /dev/sda directories from the windows side (when I boot up xp)? I've tried to look but couldn't find them. I'm just curious if that is possible. My Ubuntu installation doesn't really have a lot of exclusive files that I need to backup before redoing the whole thing over, but my xp side has a large iTunes library that I would like to  merge over to my old PowerMac933's iTunes library. XP is so loaded up with revisions and antivirus that it can't even play sound files reliably anymore without serious skipping. I would just like to dump XP altogether if I could save that music library.

---

