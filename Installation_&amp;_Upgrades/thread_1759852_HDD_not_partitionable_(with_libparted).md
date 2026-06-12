---
title: "HDD not partitionable (with libparted)"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by Karl Siegmund on 2011-05-16
Hi,

going nuts... I try to prepare a 1T SATA (@onboard Sil-controller) HDD (WD 10EADS) for installation, but all modifications (fdisk, parted, gparted) are failing (a meta-sub-sumary behavior of my 101 trys):
<- "unknown partition-table"
-> write new
<- OK
-> create partition, create p..., ...
-> write modifications:
<- [[OK, ] OK,] Error "libparted..."

+ checked the HW (S.M.A.R.T.,controller,wireing,...):
surfacescan with manufarturer tools (2): OK/no problems

+ rewrite/check MBR (# dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb)

The only (up to now) tool which works (partial), is the Win2Kpro DriveManager :( which simply does what is intended (even out of a VM)... but of course it can't format to extN.
To do (only) this last step under  [k]ubuntu 10.[10|04] guides again to the above scheme...

Any tip appreciated...
karl

---

### Post by Quackers on 2011-05-16
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rubi1200 on 2011-05-16
Was the drive part of a RAID setup previously?

Is there stray GPT data on the disk perhaps?

Posting the boot script as Quackers recommended will hopefully help us figure this out.

And welcome to the forums from me too.

---

### Post by Karl Siegmund on 2011-05-16
Hi (&thanks for your fast care),

@Rubi1200 - indeed, it was part of a hw-RAID, but I was convinced, that there are no artefacts from that time after all... but your question making me s.th. going tick-tick-tick #-o- where are mines from that typically are found and how to be sweeped?

@Quackers (...I was free, to remove not related stuff):
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spuren, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x88cc48c8

Partition  Boot         Start           End          Size  Id System

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  c9 4f 08 50 45 41 b8 48  08 84 cd c4 25 6c 4d 08  |.O.PEA.H....%lM.|
00000010  4c 88 dd 49 94 c8 c8 d6  06 ce 0d 31 8c 8e 1e c9  |L..I.......1....|
00000020  c4 c9 c0 f8 48 ca 1c 84  9c 0c 0e a8 4f dc 0c 5c  |....H.......O..\|
00000030  8e 88 c0 72 0e ce 05 ca  e5 44 f0 64 80 0c c0 80  |...r.....D.d....|
00000040  40 c0 4a 80 c6 c8 00 e0  80 8c c8 c4 c8 64 c4 34  |@.J..........d.4|
00000050  c8 84 aa 9c 4c 1c f4 c0  ec cc 2e 00 c8 0c c4 8c  |....L...........|
00000060  4d 40 08 46 5e de c4 0d  cc 88 6a c4 d8 4c c1 7c  |M@.F^.....j..L.||
00000070  80 48 4e 85 40 4a ea cc  48 9a d4 c4 4a 05 08 c8  |.HN.@J..H...J...|
00000080  53 cc 0e 8a ca ac 0c 0c  f4 84 04 cc c0 09 04 c4  |S...............|
00000090  de 48 cc 4e 5e 04 cc ce  a4 8e 44 64 80 00 5c 8c  |.H.N^.....Dd..\.|
000000a0  ce 4e 43 8e 5c 5f e0 88  ea 5c 4a cc ec 48 48 04  |.NC.\_...\J..HH.|
000000b0  04 42 48 94 13 08 cb c8  40 ca 8c ce 88 4c 5a 4a  |.BH.....@....LZJ|
000000c0  cc ac c4 78 48 20 8c 48  c5 e4 58 20 48 8c 8c 59  |...xH .H..X H..Y|
000000d0  48 c2 cc ce 10 18 c5 8c  44 80 80 4c c0 44 8c 78  |H.......D..L.D.x|
000000e0  88 e4 8c c8 d5 4a d2 c8  cc ee 88 50 8a 40 13 4c  |.....J.....P.@.L|
000000f0  53 48 80 e8 cc c0 dc c8  d9 58 48 98 c0 af c0 18  |SH.......XH.....|
00000100  88 84 c4 8e 5c 40 4a 4c  c0 c8 4c 40 ca 40 0e 88  |....\@JL..L@.@..|
00000110  8c 18 64 ac de 4a 58 ce  8a cc cd 06 84 04 d0 00  |..d..JX.........|
00000120  52 94 c0 4c c8 88 80 40  8c 48 58 4c ac cc 88 4c  |R..L...@.HXL...L|
00000130  ec dc c8 80 c0 cc 88 c6  82 88 88 c6 c8 c8 84 48  |...............H|
00000140  48 80 d4 cd ce 5c cc 4c  c8 48 ec ed a5 c8 d6 4e  |H....\.L.H.....N|
00000150  c8 78 4c 4d 49 08 40 ec  ca 4c 40 28 0d 88 04 61  |.xLMI.@..L@(...a|
00000160  e2 8c d0 5c ca 8c 42 c0  ca 08 4c c0 1a c6 02 ac  |...\..B...L.....|
00000170  84 08 8a c9 4c 6a dc cc  c1 84 c2 ea 80 84 ce ca  |....Lj..........|
00000180  8c 78 49 48 42 08 98 86  58 88 cc c2 84 dc 4c 0c  |.xIHB...X.....L.|
00000190  e3 88 9c 04 d4 dc bc 08  05 48 80 d8 cc 98 8d c4  |.........H......|
000001a0  80 ce c4 40 4c 44 c6 44  29 5e 09 c8 42 7e 88 4c  |...@LD.D)^..B~.L|
000001b0  c8 4d 0d 4c 18 6c 08 ce  c8 48 cc 88 da cc 00 00  |.M.L.l...H......|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Rubi1200 on 2011-05-16
Okay, if it was part of a RAID array and you are sure that it will no longer be used for that you can do the following from the LiveCD:
```
sudo dmraid -r -E /dev/sda
```
If this asks you to remove the metadata from a RAID drive, do so and then see if GParted or other tools can see the drive so you can partition it as you want.

---

### Post by srs5694 on 2011-05-16
If it was used in a *hardware* RAID array, then the Linux dmraid utility might not remove the old RAID data -- but I'd also expect Linux to not be bothered by the old RAID data, either. If you want to be sure the disk is completely free of old data, you can do this:

```

sudo dd if=/dev/zero of=/dev/sda

```

This command will take hours to execute, but it will *completely* wipe /dev/sda. Be *absolutely positive* you're specifying the correct device; if your computer boots from /dev/sda and you should really be wiping /dev/sdb, this command will irrecoverably trash your installation! I specified /dev/sda because your Boot Info Script output makes it look like you've only got the one disk attached.

A less radical approach would be to use either fdisk or gdisk to do the partitioning. These are text-mode tools that do *not* rely on libparted, so if libparted is flaking out for some libparted-specific reason, fdisk or gdisk should work around the problem. (fdisk should be installed by default in the Ubuntu live CD, but you'll need to install gdisk by typing "sudo apt-get install gdisk" in a Terminal window.) The fdisk utility works on old Master Boot Record (MBR) partition tables, whereas gdisk works on newer GUID Partition Tables (GPTs). On a Linux-only installation, or if your computer uses UEFI firmware, I'd go with GPT, but if you plan to install Windows on the disk *and* your computer uses BIOS, MBR will be better. Note that, on a BIOS-based computer, GPT works best if you create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) (gdisk type code EF02) of 32 KiB to 1 MiB. This is used by GRUB to improve the reliability of booting.

---

### Post by Karl Siegmund on 2011-05-16
hm...
```
sudo dmraid -r -E /dev/sdb
no raid disks and with names: "/dev/sdb"
```...no luck.

Don't be confused - I was 'on' a live CD initialy - now I'm on a temp.-HD-Installation , which became "sda".
So, the (new) target is: sdb ;-)

@srs5694 - bruteforce - hm, if nothing more elegant is found...
(in fact I'm afraid, that even this may not work ;-))
fdisk -as written- does not work at all GNU-fdisk (gdisk?) had some better results (can't remember what...)

But in fact I'm totally disapointed about this (thought to be) matured pieces of software... :-(

---

### Post by srs5694 on 2011-05-16
> **Karl Siegmund said:**
> @srs5694 - bruteforce - hm, if nothing more elegant is found...
(in fact I'm afraid, that even this may not work ;-))

Why not? If the disk has nothing but 0s written to it, then any remaining problems indicate a hardware fault. Since you say you've run SMART tests on the drive, a hardware fault seems unlikely, although possible (you could have a bad cable, for instance).

> fdisk -as written- does not work at all GNU-fdisk (gdisk?) had some better results (can't remember what...)

Saying "fdisk... does not work at all" is unhelpful. Please post your fdisk session, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings, so we can see what it's saying. It could be that fdisk's output will provide vital clues about what's going on. Please heed this point; paraphrasing programs' output, as you did in your first post, is of limited utility when troubleshooting. Providing an exact transcript of what's happened is often critical to solving problems in forums like this.

GNU fdisk is based on  libparted, so if the problem is with libparted, GNU fdisk won't help at all. IMHO, there's seldom any point to using GNU fdisk; one of the big advantages of Linux fdisk is that it's *not* based on libparted, which has quite a few limitations that fdisk doesn't share.

There's also the gdisk option. Even if you want to stick with MBR, seeing what gdisk says about the disk when you first launch it could be informative.

---

### Post by Karl Siegmund on 2011-05-16
OK - I was aware, that I have to make more documentation.

so  #1 gparted:
preperation:
[[IMG]http://img804.imageshack.us/img804/6663/gpartedpre.th.jpg[/IMG]]("http://img804.imageshack.us/img804/6663/gpartedpre.jpg")
execution&fail:
[[IMG]http://img827.imageshack.us/img827/827/gpartedmid.th.jpg[/IMG]]("http://img827.imageshack.us/img827/827/gpartedmid.jpg")
(the message [en] is: "unknown partition-table")

end:
[[IMG]http://img862.imageshack.us/img862/6113/gpartedpst.th.jpg[/IMG]]("http://img862.imageshack.us/img862/6113/gpartedpst.jpg")

details  as attachment.

#2 fdisk.distrib (...ution; not the GNU version. Sorry - german locale):
```
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0x2e1e40eb.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): o
Building a new DOS disklabel with disk identifier 0x9d6fd75e.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): w
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0x02a1ef3c.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): w
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ sudo fdisk.distrib /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): c
DOS-Kompatibilitätsflag ist nicht gesetzt

Befehl (m für Hilfe): u
Die Einheit für die Anzeige/Eingabe ist nun Sektoren

```
...after "o w" the table is stil bad(?), only the second "w" gave success...
```
[...]
Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda22e10a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1            2048     1050623      524288   83  Linux
/dev/sdb2         1050624    17827839     8388608    7  HPFS/NTFS
/dev/sdb3        17827840    51382271    16777216    7  HPFS/NTFS
/dev/sdb4        51382272  1953525167   951071448    5  Erweiterte
/dev/sdb5        51384320    57692159     3153920   82  Linux Swap / Solaris
/dev/sdb6        57694208    91248639    16777216   83  Linux
/dev/sdb7        91250688   191913983    50331648   83  Linux
/dev/sdb8       191916032  1953525167   880804568   83  Linux

Befehl (m für Hilfe): w
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0xde225424.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde225424

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe): 


```
...no errors, no complaining - simply "Groundhog Day" :confused:

> Even if you want to stick with MBR, seeing what gdisk says about the disk when you first launch it could be informative.     ```
el@Monster:~$ sudo gdisk /dev/sdb
[sudo] password for el: 
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATON IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************
```

---

### Post by srs5694 on 2011-05-16
A caveat: I don't speak German, so I'm relying ton Google translation to understand what these tools are saying. What I've gotten from these programs is intelligible, but I might have missed something because I didn't try to translate everything.

It appears to me that your disk is not reliably accepting data that's written to it. This reeks of a hardware failure. I recommend you run a SMART utility, such as smartctl or GSmartControl, and give the disk a thorough check. That will provide you with diagnostic data. (Post it here if you can't understand it -- sadly, the utilities tend to just dump a lot of technical data without much explanation.)

Even if the disk passes its SMART test, it could be that you've got a loose or bad cable, so you might try shutting down the computer and re-seating the cable at both ends. If that doesn't help, try replacing the cable with a new one.

---

### Post by Karl Siegmund on 2011-05-17
...all your thoughts have allready come to my mind this week.
Wires are already exchanged(!),  SMART-check is done... (and a lot more)

But now the impossible truth:
(sorry for more German and the M$ stuff )
missing table:
[[IMG]http://img822.imageshack.us/img822/1077/1missingptable.th.jpg[/IMG]]("http://img822.imageshack.us/img822/1077/1missingptable.jpg")
new table, partitioning, formating (all vfat/ntfs):
[[IMG]http://img204.imageshack.us/img204/3246/2tablepartformat.th.jpg[/IMG]]("http://img204.imageshack.us/img204/3246/2tablepartformat.jpg")
some drive-letters:
[[IMG]http://img845.imageshack.us/img845/5011/3drvletters.th.jpg[/IMG]]("http://img845.imageshack.us/img845/5011/3drvletters.jpg")
check properties:
[[IMG]http://img189.imageshack.us/img189/7203/4propertiesh.th.jpg[/IMG]]("http://img189.imageshack.us/img189/7203/4propertiesh.jpg")
and copy a file:
[[IMG]http://img146.imageshack.us/img146/4070/5file.th.jpg[/IMG]]("http://img146.imageshack.us/img146/4070/5file.jpg")

no changes :-k -> no errors, no problems.

Now -after that:
```
el@Monster:~$ sudo fdisk.distrib /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x143ab322

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1          65      522081    7  HPFS/NTFS
/dev/sdb2              66        1109     8385930    7  HPFS/NTFS
/dev/sdb3            1110        3198    16779892+   7  HPFS/NTFS
/dev/sdb4            3199      121601   951072097+   f  W95 Erw. (LBA)
/dev/sdb5            3199        3591     3156741    7  HPFS/NTFS
/dev/sdb6            3592        5680    16779861    7  HPFS/NTFS
/dev/sdb7            5681       11946    50331613+   7  HPFS/NTFS
/dev/sdb8           11947      121601   880803756    7  HPFS/NTFS


```Lets try:
```
Befehl (m für Hilfe): t
Partitionsnummer (1-8): 5
Hex code (L um eine Liste anzuzeigen): 82
Der Dateisystemtyp der Partition 5 ist nun 82 (Linux Swap / Solaris)

Befehl (m für Hilfe): t 6
Partitionsnummer (1-8): 6
Hex code (L um eine Liste anzuzeigen): 83
Der Dateisystemtyp der Partition 6 ist nun 83 (Linux)

Befehl (m für Hilfe): t
Partitionsnummer (1-8): 7
Hex code (L um eine Liste anzuzeigen): 83
Der Dateisystemtyp der Partition 7 ist nun 83 (Linux)

Befehl (m für Hilfe): t
Partitionsnummer (1-8): 8
Hex code (L um eine Liste anzuzeigen): 83
Der Dateisystemtyp der Partition 8 ist nun 83 (Linux)

Befehl (m für Hilfe): t
Partitionsnummer (1-8): 1
Hex code (L um eine Liste anzuzeigen): 83
Der Dateisystemtyp der Partition 1 ist nun 83 (Linux)

Befehl (m für Hilfe): w
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.

``````
el@Monster:~$ sudo fdisk.distrib /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x143ab322

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1          65      522081   83  Linux
/dev/sdb2              66        1109     8385930    7  HPFS/NTFS
/dev/sdb3            1110        3198    16779892+   7  HPFS/NTFS
/dev/sdb4            3199      121601   951072097+   f  W95 Erw. (LBA)
/dev/sdb5            3199        3591     3156741   82  Linux Swap / Solaris
/dev/sdb6            3592        5680    16779861   83  Linux
/dev/sdb7            5681       11946    50331613+  83  Linux
/dev/sdb8           11947      121601   880803756   83  Linux

```So, only need to format partitions...

[[IMG]http://img42.imageshack.us/img42/1791/6gpartedpre.th.jpg[/IMG]]("http://img42.imageshack.us/img42/1791/6gpartedpre.jpg")
[[IMG]http://img801.imageshack.us/img801/4945/7gpartedmid.th.jpg[/IMG]]("http://img801.imageshack.us/img801/4945/7gpartedmid.jpg")

 |-->part II

---

### Post by Karl Siegmund on 2011-05-17
[part II]

[[IMG]http://img820.imageshack.us/img820/3880/8gpartedpst.th.jpg[/IMG]]("http://img820.imageshack.us/img820/3880/8gpartedpst.jpg")

maybe there is a problem is in the mkfs.* or gparted refreshes (=kills) the partiontable after every format.
I will try to do all again (later not today - it's 10:15 am local time here) using the mkfs.* directly on the console...

---

### Post by srs5694 on 2011-05-17
Trying it using the text-mode tools (mkfs, etc.) is certainly worthwhile. I still think you've got a hardware problem, though; or maybe it's a driver problem or a problem with access modes (more on that below). The sorts of symptoms you're seeing are those that I expect to see in certain types of hardware problems, but not in software problems. In any event, it's also worth looking at the kernel ring buffer before and after you encounter an error when accessing the disk. Type "dmesg | tail" to see the last few kernel ring buffer messages, then do something that's likely to provoke a failure, and then type "dmesg | tail" again. Compare the two dmesg outputs. If there are any new messages, they were probably the result of your failed attempt, and may contain clues. (It's conceivable that something unrelated will happen to have worked its way into the kernel ring buffer, but such unrelated messages should be easy to spot and ignore.)

The access mode issue is one of BIOS settings for AHCI mode or other disk-related options. You could check your BIOS settings related to the disk and try fiddling with these settings. Sometimes Linux works better with one setting or another, so you may need to adjust them. OTOH, if you change such a setting, it could upset Windows, so you might have to re-install Windows from scratch. You can certainly test the effect on Linux without booting Windows, and if a change has a beneficial effect, do a Web search or ask on a Windows forum about its likely effect in Windows.

One more comment: One of your many screen shots shows GParted's view of the disk as partitioned in Windows. GParted could not identify the filesystems used on partitions 1, 2, 3, 5, 6, or 8, despite the fact that you'd created these as NTFS partitions in Windows. GParted can normally identify NTFS quite reliably (and it did in that screen shot for partition 7). This tells me that you've got a problem *reading* data, as well as (or perhaps instead of) *writing* it.

---

### Post by Karl Siegmund on 2011-05-17
> **srs5694 said:**
> Trying it using the text-mode tools (mkfs, etc.) is certainly worthwhile. I still think you've got a hardware problem, though; or maybe it's a driver problem or a problem with access modes (more on that below). The sorts of symptoms you're seeing are those that I expect to see in certain types of hardware problems, but not in software problems.
I fear yoou're right - I would have checked this, but this is actually the only SATA-System on hand.
I thought about purchaising a SATA-controller for a X-check... (stuck in HCL-search... you may have a tip?)
> **srs5694 said:**
> In any event, it's also worth looking at the kernel ring buffer before and after you encounter an error when accessing the disk. Type "dmesg | tail" to see the last few kernel ring buffer messages, then do something that's likely to provoke a failure, and then type "dmesg | tail" again. Compare the two dmesg outputs. If there are any new messages, they were probably the result of your failed attempt, and may contain clues. (It's conceivable that something unrelated will happen to have worked its way into the kernel ring buffer, but such unrelated messages should be easy to spot and ignore.)
Indeed, but nothing usable - see yourself (I inserted some [[COLOR=Blue]free translations][/COLOR])[COLOR=Blue]:[/COLOR]
```
el@Monster:~$ dmesg |tail
[71599.273721] bridge-eth1: disabled promiscuous mode
[71599.273806] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273823] device eth1 entered promiscuous mode
[71599.273941] bridge-eth1: enabled promiscuous mode
[71599.273944] /dev/vmnet: port on hub 0 successfully opened
[71599.273959] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273967] /dev/vmnet: port on hub 0 successfully opened
[73043.009929]  sdb: sdb1
[74510.640131] device eth1 left promiscuous mode
[74510.640255] bridge-eth1: disabled promiscuous mode
el@Monster:~$ sudo fdisk.distrib /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3eb1742e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe): o
Building a new DOS disklabel with disk identifier 0x2cddb29c.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges [COLOR=Red]Flag 0x0000 in Part.-tabelle 4[/COLOR] korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): w
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ dmesg |tail
[71599.273806] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273823] device eth1 entered promiscuous mode
[71599.273941] bridge-eth1: enabled promiscuous mode
[71599.273944] /dev/vmnet: port on hub 0 successfully opened
[71599.273959] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273967] /dev/vmnet: port on hub 0 successfully opened
[73043.009929]  sdb: sdb1
[74510.640131] device eth1 left promiscuous mode
[74510.640255] bridge-eth1: disabled promiscuous mode
[92841.669792]  [COLOR=Red]sdb: unknown partition table[/COLOR]
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0x29aedcdb.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): c
DOS-Kompatibilitätsflag ist nicht gesetzt

Befehl (m für Hilfe): u
Die Einheit für die Anzeige/Eingabe ist nun Sektoren

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29aedcdb

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe): n 
Befehl  Aktion
   e      Erweiterte
   p      Primäre Partition (1-4)
p
Partitionsnummer (1-4): 1
Erster Sektor (2048-1953525167, Vorgabe: 2048): 
Benutze den Standardwert 2048
Last Sektor, +Sektoren or +size{K,M,G} (2048-1953525167, Vorgabe: 1953525167): +512M           

Befehl (m für Hilfe): n
Befehl  Aktion
   e      Erweiterte
   p      Primäre Partition (1-4)
p
Partitionsnummer (1-4): 2
Erster Sektor (1050624-1953525167, Vorgabe: 1050624): 
Benutze den Standardwert 1050624
Last Sektor, +Sektoren or +size{K,M,G} (1050624-1953525167, Vorgabe: 1953525167): +8192M

Befehl (m für Hilfe): n
Befehl  Aktion
   e      Erweiterte
   p      Primäre Partition (1-4)
p
Partitionsnummer (1-4): 3
Erster Sektor (17827840-1953525167, Vorgabe: 17827840): 
Benutze den Standardwert 17827840
Last Sektor, +Sektoren or +size{K,M,G} (17827840-1953525167, Vorgabe: 1953525167): +16384M

Befehl (m für Hilfe): n
Befehl  Aktion
   e      Erweiterte
   p      Primäre Partition (1-4)
e
Partition 4 ausgewählt
Erster Sektor (51382272-1953525167, Vorgabe: 51382272): 
Benutze den Standardwert 51382272
Last Sektor, +Sektoren or +size{K,M,G} (51382272-1953525167, Vorgabe: 1953525167): 
Benutze den Standardwert 1953525167

Befehl (m für Hilfe): n
Erster Sektor (51384320-1953525167, Vorgabe: 51384320): 
Benutze den Standardwert 51384320
Last Sektor, +Sektoren or +size{K,M,G} (51384320-1953525167, Vorgabe: 1953525167): +3080M

Befehl (m für Hilfe): n
Erster Sektor (57694208-1953525167, Vorgabe: 57694208): 
Benutze den Standardwert 57694208
Last Sektor, +Sektoren or +size{K,M,G} (57694208-1953525167, Vorgabe: 1953525167): +16384M

Befehl (m für Hilfe): n
Erster Sektor (91250688-1953525167, Vorgabe: 91250688): 
Benutze den Standardwert 91250688
Last Sektor, +Sektoren or +size{K,M,G} (91250688-1953525167, Vorgabe: 1953525167): +49152M

Befehl (m für Hilfe): n
Erster Sektor (191916032-1953525167, Vorgabe: 191916032): 
Benutze den Standardwert 191916032
Last Sektor, +Sektoren or +size{K,M,G} (191916032-1953525167, Vorgabe: 1953525167): 
Benutze den Standardwert 1953525167

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29aedcdb

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1            2048     1050623      524288   83  Linux
/dev/sdb2         1050624    17827839     8388608   83  Linux
/dev/sdb3        17827840    51382271    16777216   83  Linux
/dev/sdb4        51382272  1953525167   951071448    5  Erweiterte
/dev/sdb5        51384320    57692159     3153920   83  Linux
/dev/sdb6        57694208    91248639    16777216   83  Linux
/dev/sdb7        91250688   191913983    50331648   83  Linux
/dev/sdb8       191916032  1953525167   880804568   83  Linux

Befehl (m für Hilfe): q

el@Monster:~$ dmesg |tail
[71599.273806] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273823] device eth1 entered promiscuous mode
[71599.273941] bridge-eth1: enabled promiscuous mode
[71599.273944] /dev/vmnet: port on hub 0 successfully opened
[71599.273959] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273967] /dev/vmnet: port on hub 0 successfully opened
[73043.009929]  sdb: sdb1
[74510.640131] device eth1 left promiscuous mode
[74510.640255] bridge-eth1: disabled promiscuous mode
[92841.669792]  [COLOR=DarkRed]sdb: unknown partition table[/COLOR]
el@Monster:~$ sudo mkfs.ext2 -T 82 /dev/sdb1
mke2fs 1.41.12 (17-May-2010)
Status für /dev/sdb1 konnte nicht ermittelt werden --- Datei oder Verzeichnis nicht gefunden
[COLOR=Blue]["Couldn't get state of /dev/sdb1 --- file or directory not found"][/COLOR]

Das Gerät existiert offensichtlich nicht; haben Sie es richtig angegeben?
[COLOR=Blue]["The device doesn't exists - typo?"][/COLOR]
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
[COLOR=Blue]["neither valid DOS-partition table nor... disclable"][/COLOR]
Building a new DOS disklabel with disk identifier 0x08866b0e.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08866b0e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe): w   
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ sudo fdisk.distrib /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08866b0e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe): w   
Die Partitionstabelle wurde verändert!

Rufe ioctl() um Partitionstabelle neu einzulesen.
Synchronisiere Platten.
el@Monster:~$ dmesg |tail
[71599.273941] bridge-eth1: enabled promiscuous mode
[71599.273944] /dev/vmnet: port on hub 0 successfully opened
[71599.273959] /dev/vmnet: open called by PID 12828 (vmware-vmx)
[71599.273967] /dev/vmnet: port on hub 0 successfully opened
[73043.009929]  sdb: sdb1
[74510.640131] device eth1 left promiscuous mode
[74510.640255] bridge-eth1: disabled promiscuous mode
[92841.669792]  [COLOR=DarkRed]sdb: unknown partition table[/COLOR]
[93230.491712]  [COLOR=Red]sdb:[/COLOR]
[93244.433838]  [COLOR=Red]sdb:[/COLOR]
el@Monster:~$ 

```Not very enlightening to me ;-)

> **srs5694 said:**
> 
The access mode issue is one of BIOS settings for AHCI mode or other disk-related options. You could check your BIOS settings related to the disk and try fiddling with these settings. Sometimes Linux works better with one setting or another, so you may need to adjust them. OTOH, if you change such a setting, it could upset Windows, so you might have to re-install Windows from scratch. You can certainly test the effect on Linux without booting Windows, and if a change has a beneficial effect, do a Web search or ask on a Windows forum about its likely effect in Windows.
No, the onboard SATA-Controller has its own Bios, only configurable for/in hw-RAID functionality.
The  Win* partitions are only for emergency or spare purposes.
In the last time VMs have taken the place of my dual-/multi -boot installations...

> **srs5694 said:**
> One more comment: One of your many screen shots shows GParted's view of the disk as partitioned in Windows. GParted could not identify the filesystems used on partitions 1, 2, 3, 5, 6, or 8, despite the fact that you'd created these as NTFS partitions in Windows. GParted can normally identify NTFS quite reliably (and it did in that screen shot for partition 7). This tells me that you've got a problem *reading* data, as well as (or perhaps instead of) *writing* it.
Yes,  I remember the situation... Even in Windows, the mounting of the just formated partitions needed some convincing actions... and finally only the writing of the 'testfile' seems to get the *haptic* as usual.
So I wasn't astonished, that only drive H: was visible...

---

### Post by Karl Siegmund on 2011-05-17
So, we start with a PT made by Win.:
```
el@Monster:~$ sudo fdisk.distrib /dev/sdb
[sudo] password for el:

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x146dafd8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1          65      522081    b  W95 FAT32
/dev/sdb2              66        1109     8385930    7  HPFS/NTFS
/dev/sdb3            1110        3198    16779892+   7  HPFS/NTFS
/dev/sdb4            3199      121601   951072097+   f  W95 Erw. (LBA)
/dev/sdb5            3199        3591     3156741    b  W95 FAT32
/dev/sdb6            3592        5680    16779861    7  HPFS/NTFS
/dev/sdb7            5681       11946    50331613+   7  HPFS/NTFS
/dev/sdb8           11947      121601   880803756    7  HPFS/NTFS

Befehl (m für Hilfe): v
Remaining 5413 unallocated 512-byte sectors

Befehl (m für Hilfe): q

```But all VFAT and all in the extended-P. have to (re-)formated to ext# fs.

So we start with (Bootloader/Grub/) sdb1 - sorry for the german  (better: "Genglish"),
it's only the verbose how/what is done... you may note: "...größe" = "-size", "Datei" = "File",
"erledigt" = "done". 
```
el@Monster:~$ sudo mkfs.ext2 /dev/sdb1
mke2fs 1.41.12 (17-May-2010)
Dateisystem-Label=
OS-Typ: Linux
Blockgröße=1024 (log=0)
Fragmentgröße=1024 (log=0)
Stride=0 Blöcke, Stripebreite=0 Blöcke
130560 Inodes, 522080 Blöcke
26104 Blöcke (5.00%) reserviert für den Superuser
Erster Datenblock=1
Maximale Dateisystem-Blöcke=67633152
64 Blockgruppen
8192 Blöcke pro Gruppe, 8192 Fragmente pro Gruppe
2040 Inodes pro Gruppe
Superblock-Sicherungskopien gespeichert in den Blöcken: 
        8193, 24577, 40961, 57345, 73729, 204801, 221185, 401409

Schreibe Inode-Tabellen: erledigt                        
Schreibe Superblöcke und Dateisystem-Accountinginformationen: erledigt

Das Dateisystem wird automatisch nach jeweils 24 Einhäng-Vorgängen bzw.
alle 180 Tage überprüft, je nachdem, was zuerst eintritt. Dies kann durch
tune2fs -c oder -i geändert werden.
```...everything seems fine, but.
```
el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0x568da6af.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x568da6af

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe):

```again the PT seems to be corrupted!?
I opend the Wndows 2000pro DriveManager again which shows an undifferentiated  picture - explainable by the unknown ext2  fs... but this sole opening  fixed s.th.:

```
el@Monster:~$ sudo fdisk.distrib /dev/sdb
[sudo] password for el: 

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x146dafd8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1          65      522081    b  W95 FAT32
/dev/sdb2              66        1109     8385930    7  HPFS/NTFS
/dev/sdb3            1110        3198    16779892+   7  HPFS/NTFS
/dev/sdb4            3199      121601   951072097+   f  W95 Erw. (LBA)
/dev/sdb5            3199        3591     3156741    b  W95 FAT32
/dev/sdb6            3592        5680    16779861    7  HPFS/NTFS
/dev/sdb7   ?        5681       11946    50331613+   7  HPFS/NTFS
/dev/sdb8           11947      121601   880803756    7  HPFS/NTFS


```any idea what the "?" for the boot-flag and the "+" in the column 'blocks' (="Blöcke") mean?

a "w"rite fixed the "?"...

But the formating:
```
el@Monster:~$ sudo mkfs.ext2 /dev/sdb1
mke2fs 1.41.12 (17-May-2010)
Dateisystem-Label=
OS-Typ: Linux
Blockgröße=1024 (log=0)
Fragmentgröße=1024 (log=0)
Stride=0 Blöcke, Stripebreite=0 Blöcke
130560 Inodes, 522080 Blöcke
26104 Blöcke (5.00%) reserviert für den Superuser
Erster Datenblock=1
Maximale Dateisystem-Blöcke=67633152
64 Blockgruppen
8192 Blöcke pro Gruppe, 8192 Fragmente pro Gruppe
2040 Inodes pro Gruppe
Superblock-Sicherungskopien gespeichert in den Blöcken:
        8193, 24577, 40961, 57345, 73729, 204801, 221185, 401409

Schreibe Inode-Tabellen: erledigt
Schreibe Superblöcke und Dateisystem-Accountinginformationen: erledigt

Das Dateisystem wird automatisch nach jeweils 24 Einhäng-Vorgängen bzw.
alle 180 Tage überprüft, je nachdem, was zuerst eintritt. Dies kann durch
tune2fs -c oder -i geändert werden.
```crashes the PT as any other write operation:
```

el@Monster:~$ sudo fdisk.distrib /dev/sdb
Das Gerät enthält weder eine gültige DOS-Partitionstabelle,
noch einen „Sun“, „SGI“ oder „OSF disklabel“
Building a new DOS disklabel with disk identifier 0x568da6af.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warnung: Schreiben wird ungültiges Flag 0x0000 in Part.-tabelle 4 korrigieren

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Befehl (m für Hilfe): p

Platte /dev/sdb: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x568da6af

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Befehl (m für Hilfe):

```

---

### Post by srs5694 on 2011-05-17
It sounds like any attempt to write (and perhaps read) data to(/from) the disk is unreliable, and may even be overwriting the wrong sectors. I have a few more ideas at this point:


[list]
[*]Try connecting the hard disk to another connector on the motherboard or disk controller. It's possible the one you're using is bad -- it could be defective or it could be using a different controller than you're using on your main disk. (Some motherboards use a primary disk controller for some devices and then have a secondary controller for additional devices. Sometimes one of these controllers works well under Linux but another has no or buggy drivers.)
[*]If you've got a spare drive, try connecting it in place of the one that's giving you problems. If *it* malfunctions, then you can narrow the scope of your search to exclude the hard disk. If the replacement disk is OK, then chances are your hard disk itself is bad.
[*]Try the hard disk you're trying to use in another computer. Like the previous test, this should help you narrow down the scope of the problem.
[*]Try using other partitioning tools -- GNU Parted (command name parted) and gdisk -- to write partition tables to the disk. They might fare no better than fdisk, but they might produce different patterns of problems or helpful error messages. Note that gdisk produces GUID Partition Tables (GPTs). This could actually be helpful, since GPT includes CRCs to help detect data corruption. OTOH, if you want to use MBR on the disk, you'll have to be sure to completely wipe the GPT data if/when you resolve the problem and partition it "for real." (This isn't difficult; you can use the "z" option on gdisk's experts' menu or create a new partition table using parted or GParted.) You can also use parted to create or edit GPTs, so you could use it both ways.
[*]Try contacting the disk's manufacturer. They may have suggestions for fixes or additional tests you can run.
[/list]

---

### Post by Lanser on 2011-05-18
Karl. I have had this scenario many times as I formed then broke up RAID arrays.
I think you will find that your issue is at the hardware / firmware level on the drives.

The RAID utility you used to build the array, has made changes to the way the data is written. The only way I have found to re-utilize drives from arrays is to use the same utility that created them to change them back to stand alone mode. 
There are a number of flags set in the firmware that need to be changed. 

hope this helps

Lanser

---

