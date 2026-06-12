---
title: "Is this Ubuntu 14.04 recoverable?"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by jdnevarez on 2015-11-01
I run the Repair boot utility and report at 
[http://paste.ubuntu.com/13060214/](http://paste.ubuntu.com/13060214/)

Can someone please tell me if this something I can recover or I need to reinstall Ubuntu?

Please advice

---

### Post by Bucky Ball on 2015-11-01
Welcome. Well, you appear to have nothing on drive sda and one large EFI FAT32 partition on sdb, so unsure what you have done here. There is no Ubuntu installed that I can see. 

Also have no idea what these are:

```
/dev/zram0: UUID="b10b3d76-c14b-49c0-a338-58fbbfe05ea5" TYPE="swap"
/dev/zram1: UUID="0b608b5a-04b6-4644-87d1-f018c3cb8f4f" TYPE="swap"
/dev/zram2: UUID="5f1abac1-d318-42ea-ac2c-dfef612cfde4" TYPE="swap"
/dev/zram3: UUID="47591cb5-3bb4-4f96-b586-b5279b62e273" TYPE="swap"
```

Hopefully someone can enlighten us ... :-k

Please let us know what exactly you were trying to do. Did you have Ubuntu installed already, did something, and now it doesn't work, or are you trying to install Ubuntu on a disk from scratch, no Windows dual-boot  (as this is in ***Installations and Upgrades*** I'm presuming this is the case)?

---

### Post by jdnevarez on 2015-11-01
Yes I used to have Ubuntu 14.04 LTS 64 bit running, I was creating some yocto images, so my guess is that I flashed to the wrong /dev/sd> by mistake, but not sure because I reuse a command from history since I was doing it several times a day.
So for now I leaving the HD alone and reinstalling Ubuntu on a second drive with the hope that my installation can be recovered with  the help of some savvy people here.
Thanks for our reply Bucky Ball

---

### Post by Bucky Ball on 2015-11-01
That's fine, but there is no installation on the sda disk. There is nothing there. sdb is the Boot Repair disk/USB? Take a look at this:

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,827,455     7,825,408   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        5657-EB7D                              vfat       BOOT-REPAIR
/dev/zram0       b10b3d76-c14b-49c0-a338-58fbbfe05ea5   swap       
/dev/zram1       0b608b5a-04b6-4644-87d1-f018c3cb8f4f   swap       
/dev/zram2       5f1abac1-d318-42ea-ac2c-dfef612cfde4   swap       
/dev/zram3       47591cb5-3bb4-4f96-b586-b5279b62e273   swap 
```

See the first entry for sda? There is nothing there, no partitions, nothing. Look in the 'blkid' output. sda does not even rate a mention. I don't think there is any retrieving your install as there isn't one there. About your only hope would be to stop using that drive immediately and try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

Good luck and perhaps someone else can throw in other ideas, but it looks grim to me. :|

---

### Post by jdnevarez on 2015-11-01
Thanks a lot, I was hoping for a miracle, because yes I saw sda with no partitions, it seems Ubuntu was wiped out.
Oh well I better start a new Installation right away. Thanks for making the time to look at the report and your support here.

---

### Post by Bucky Ball on 2015-11-01
All good and good luck. Please mark as solved (first link in my signature) and start a new thread if you hit any future brickwalls. ;)

---

