---
title: "Please help, no Windows 7 in boot menu"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by w1n32 on 2012-02-10
I have been using Ubuntu 11.04 and today I install 11.10 x64 inn dual boot with Windows 7 x64.
Afther I install 11.10 I can't see Windows 7 in boot menu.
I try to fix that with Windows 7 CD and I can't do anything.
Afther that I try to fix MBR with Boot Repair from Ubuntu but I can't see Windows 7 when I go in Advanced options -> Restore the MBR from -> Partition booted by the MBR-> I can't find Windows 7 here

I have 3 x 1 TB HDD.

Please help because I realy don't know what to do.

Here's log of Boot Repair:

                                  [http://paste.ubuntu.com/836885/](http://paste.ubuntu.com/836885/)

When I enter in terminal *sudo fdisk -l* I get this:



Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec24af94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         8064691  1812212324   902073817    f  W95 Ext'd (LBA)
/dev/sda2   *  1812213760  1851277311    19531776   83  Linux
/dev/sda3      1851277312  1929402367    39062528   83  Linux
/dev/sda4      1929402368  1945028607     7813120   82  Linux swap / Solaris
/dev/sda5         8064693  1812212324   902073816    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12131212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   156165839    77979496    7  HPFS/NTFS/exFAT
/dev/sdb3       156165840  1953524789   898679475    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c92a0d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

---

### Post by cortman on 2012-02-10
Have you tried to update grub? Boot into Ubuntu, open a terminal, and type

```
sudo update-grub
```

---

### Post by darkod on 2012-02-10
You are missing the /boot/BCD folder on sdb1. Without boot files to detect, it's not creating an entry for win7.

Also, why are you mounting that partition in /etc/fstab? There is nothing useful there and you can only create problems if you touch the win7 boot files by mistake.

The win7 disc should be able to repair this. You can also try unplugging the other two disks and try the repair with only win7 connected.
If the auto process doesn't work you can also try the command prompt approach. And sometimes it takes win7 repair to run 3 or 4 times before it repairs all of the boot process. Don't stop at running it only once.

---

### Post by w1n32 on 2012-02-10
> **cortman said:**
> Have you tried to update grub? Boot into Ubuntu, open a terminal, and type

```
sudo update-grub
```

Yes, I try that and nothing.
Then I only get this:

Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin

Windows partition is ok and when i put fdisk -l I get this:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec24af94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         8064691  1812212324   902073817    f  W95 Ext'd (LBA)
/dev/sda2   *  1812213760  1851277311    19531776   83  Linux
/dev/sda3      1851277312  1929402367    39062528   83  Linux
/dev/sda4      1929402368  1945028607     7813120   82  Linux swap / Solaris
/dev/sda5         8064693  1812212324   902073816    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12131212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   156165839    77979496    7  HPFS/NTFS/exFAT
/dev/sdb3       156165840  1953524789   898679475    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c92a0d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

---

### Post by w1n32 on 2012-02-10
> **darkod said:**
> You are missing the /boot/BCD folder on sdb1. Without boot files to detect, it's not creating an entry for win7.

Also, why are you mounting that partition in /etc/fstab? There is nothing useful there and you can only create problems if you touch the win7 boot files by mistake.

The win7 disc should be able to repair this. You can also try unplugging the other two disks and try the repair with only win7 connected.
If the auto process doesn't work you can also try the command prompt approach. And sometimes it takes win7 repair to run 3 or 4 times before it repairs all of the boot process. Don't stop at running it only once.

I try repair with disc of Win 7 and nothing. 

Now I try ad this:

menuentry "Windows 7" {
set root=(hd1,1)
chainloader +1
}

...and hd1,0 and lot of other options and nothing.

---

### Post by collisionystm on 2012-02-10
can you see your windows 7 files?

try

sudo update-grub2

---

### Post by darkod on 2012-02-10
> **w1n32 said:**
> I try repair with disc of Win 7 and nothing. 

Now I try ad this:

menuentry "Windows 7" {
set root=(hd1,1)
chainloader +1
}

...and hd1,0 and lot of other options and nothing.

Did you try it at least three times in a row?

Adding an entry for win7 won't do anything, part of the boot files are missing. Grub won't be able to boot it. That's why it doesn't show it.

Google around for different ways to recover win7 boot files (that worked) and try them, but with care. This is only windows related problem. As soon as you solve the missing files, doing the update-grub will show it.

---

### Post by w1n32 on 2012-02-10
> **collisionystm said:**
> can you see your windows 7 files?

try

sudo update-grub2

Yes, Windows 7 file is here.
I try and sudo update-grub2...and nothing.

> **darkod said:**
> Did you try it at least three times in a row?

Adding an entry for win7 won't do anything, part of the boot files are missing. Grub won't be able to boot it. That's why it doesn't show it.

Google around for different ways to recover win7 boot files (that worked) and try them, but with care. This is only windows related problem. As soon as you solve the missing files, doing the update-grub will show it.

Yes, I try 5-6 times but nothing.

Here's SS of from Disk Util.

[http://i.imgur.com/Vx1tf.png](http://i.imgur.com/Vx1tf.png)

---

