---
title: "Lost Partition???"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by BuffaloX on 2006-06-06
I originally installed from AMD-64 alternate on primary sata drive.
Because some programs doesn't work in 64 bit version, I decided to make an i386
2nd ubuntu, on my secondary sata harddrive. (Which has my XP also)
I used ubuntu 6.06 desktop. Chose 2nd drive, then use free space.
I had shrinked my XP partition, to make room for this, I was able to free up 50 GB of unallocated disk space.

But now I can't boot the original 64 bit installation, only the new i386 ubuntu appears in my boot menu.
If I look in Boot menu.lst, there is no mention of my old installation.

Disk manager states my 64bit anstallation as unformatted. 
Gnome partition edit, states the old partition as unknown format.
This was an ext3 patition...

1) Is my original data and installation lost?
2) Can I dual boot Ubuntu AMD64 / i386, as I originally planned?

---

### Post by thomashauk on 2006-06-06
Seems odd. If it coming up with unknown format is sounds corrupted.
Chould you give your partition stucture so I can see what is going on?

---

### Post by BuffaloX on 2006-06-06
Sure Partitions are as follow: (according to Disks Manager)

SDA: Partition 5 - 243 MiB Extended 3
         Partition 6 - 69 GiB unformatted

SDB: Partition 1 - 30 GiB NTFS
         Partition 5 - 100 GiB NTFS
         SWAP 2.3 GiB
         Partition 3 - 53 GiB Extended 3

Which make me wonder, shouldn't there be both a Swap and Ext 3 on SDA?
Seems like the installation totally blanked my SDA drive. :( 
Although I specifically selected SDB for installation.

---

