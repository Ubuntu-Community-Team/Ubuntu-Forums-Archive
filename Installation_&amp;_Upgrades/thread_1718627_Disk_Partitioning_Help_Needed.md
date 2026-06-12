---
title: "Disk Partitioning Help Needed"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by Tchoob on 2011-03-31
I'm trying to dual boot Windows 7 and Ubuntu. I've been using Ubuntu for a while now, but I need Windows 7 as well for school. I have a 500 gigabyte hard drive, and want to allocate 200 gigs to Windows 7. I put in the Windows 7 install disk I was given, go to custom install, and tried to partition the drive from there, but it wouldn't let me because the disk wasn't NTFS.

I then tried to change the disk type to NTFS from Linux via Disk Utility, and it appeared to be working, but then nothing happened.

Really what I'm trying to do here is divide the partition I'm currently using into two partitions, one being 200g and the other being 300g. I then need to change the 200g partition to the NTFS file format. I need this done by tomorrow so help would be greatly appreciated.

---

### Post by vanadium on 2011-03-31
You can change the partitioning of a drive using the utility gparted. With it, you can reduce the size of partitions, then create new partitions in the freed space.

Because you are changing your system drive, you cannot do that from within your regular Ubuntu install. Instead, start up a live session from the installation CD. The live session has gparted available by default. Start it by pressing F2, then typing "gparted".

How exactly you could repartition is not possible to say: for this, we need to know your current partitioning scheme. You can obtain it from the command "sudo fdisk -l" and post it here.

---

### Post by Hedgehog1 on 2011-03-31
[FONT=Times New Roman][SIZE=3]The best way for us to see all the partitons on your disk (Windows and Ubuntu) is this:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please boot off the LiveCD/LiveUSB, select 'TRY', and then:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Follow the instruction on the website and post the results here.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]***The Hedge***[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]:KS[/SIZE][/FONT]

---

### Post by vanadium on 2011-04-01
It is as simple as putting on your computer, then Applications - Accessories - Terminal, then typing
```

sudo fdisk -l

```
No need to download a CD, burn it and boot your computer with it.

---

