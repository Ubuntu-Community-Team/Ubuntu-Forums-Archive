---
title: "Installation corrupt, what to do?"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by scampioen on 2011-08-21
Hi,
I recently tried to install Ubuntu on an old computer (about 6 or 7 years old), with an install disc i made following the instruction on the Ubuntu site. Everything was going well, untill at about 3/4 of the installation the program just crashed. There was a message saying there was an error and that it could be because the computer was old and the disc was burned too fast.

I tried again multiple times with this installation disc and one burned at lower speeds. The installation program loads, but only the welcoming, introductory and thank you messages appear. It also gives a few errors (about a file thats missing). There is no installation bar. It just seems to freeze. The computer wont start up without the Ubuntu installation disc inserted. 

I hope you can help me. Btw, this is my first time ever trying out Linux. 
Thank You

---

### Post by sanderd17 on 2011-08-21
What are the specs of your computer? To run a live CD you need at least 512 MB ram, and even that will give you a bad experience.

If you still want to try Linux on that computer, I would suggest [Lubuntu]("http://lubuntu.net/") (the ease of Ubuntu, but with a lighter graphical environment). Or even[ puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") (very fast, but not so easy to install custom applications and change settings).

---

### Post by scampioen on 2011-08-21
It has atleast 512. Perhaps it even has 1gb, im not sure. It's a Pentium 4. It was custom bought pre-made (brand: Medion).

---

### Post by sanderd17 on 2011-08-21
Hmm, I also have a Medion, P4 and 1GB of RAM (probably bought about the same time). And Mint 10 (Ubuntu 10.10 based) runs fine on it.

Do you have another computer so that you can check the md5 checksum? 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The checksum of the CD should be the same as the corresponding one here: [http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.04/release/](http://ftp.heanet.ie/pub/ubuntu-cdimage/releases/11.04/release/)

---

### Post by scampioen on 2011-08-21
I checked the file i burned, that one checks out. 
How to i check the Cd's? Which part of the cd do i need to check? I can't find an iso file on it.

---

### Post by sanderd17 on 2011-08-21
you need to check the CD as a whole. But I don't know how to do that easy on Windows.

What you can do is, when your CD boots up, press a key at the first purple screen. Then you will get into a basic menu where you can choose to check the CD.

---

### Post by scampioen on 2011-08-24
Well, i just reinstalled Windows XP on it, so now the computer can atleast boot up. 
So how do i proceed if i want Ubuntu on it without problems now? Go with the lighter interface thing?

---

### Post by sanderd17 on 2011-08-24
Could you first boot up a live CD and post the output of the boot info script? Follow the instructions here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Booting a live CD worked right? It was only installing that didn't work.

I just want to see how good your XP installation went, and if Ubuntu left any things on your computer that you need to get rid of first.

You can certainly try a lighter version like Lubuntu. If lubuntu works, you can still install other desktop environments next to it.

---

### Post by scampioen on 2011-08-24
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   389,672,639   389,672,577   7 NTFS / exFAT / HPFS
/dev/sda2         389,675,006   390,721,535     1,046,530   5 Extended
/dev/sda5         389,675,008   390,721,535     1,046,528  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4194 MB, 4194304000 bytes
255 heads, 63 sectors/track, 509 cylinders, total 8192000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     8,191,999     8,191,936   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        10AC60A0AC608258                       ntfs       
/dev/sda5        546c5d13-bf23-4aac-bfbd-533971d5e875   swap       
/dev/sdb1        0CDB-F57C                              vfat       USB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/10AC60A0AC608258  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/USB               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
--------------------------------------------------------------------------------


This is what i got, hope it's safe to install now.

---

### Post by sanderd17 on 2011-08-24
It should be OK. You still have an extended partition and swap, those are leftovers from your Ubuntu installation, but I don't think they will cause problems. You can delete those two partitions in gparted (via the live CD) if you want, but you don't need to.

Installing Lubuntu will be safe.

---

### Post by scampioen on 2011-08-25
Ok i tried to install Lubuntu. I first selected "check cd for errors" option. CD was fine.
But when i tried to install i get the error message "Kernel Panic - not syncing. Attemped to kill init!" and then abit of text and numbers after that. 

Whats happening now...?

---

