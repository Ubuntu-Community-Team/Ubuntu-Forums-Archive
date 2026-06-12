---
title: "exception Emask 0x0 .... error when booting 14.10 x64"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by bkocian on 2015-03-20
Attached error message.  Linux mint (ubuntu 14.04 variants) boot fine but 14.10 stops dead at this error.  The liveUSB boot 14.10 works ok though (though the nouveau driver makes it barely usable).

specs:
Ancient Athlon 64 3000+ (supports PAE, SSE2, but not CompareExchange128)
3 gig ram
GF 6200 AGP 512mb

Does anyone know what this error is related to?

[ATTACH=CONFIG]260774[/ATTACH]

---

### Post by Bashing-om on 2015-03-20
bkocian; Hi ! Welcome to the forum;

I have no knowledge as to the DMA error, however the ALERT! condition is generally that grub (GRand Uninified Bootloader) can not find it's config files. Related ?
Maybe we can find out, and help grub to complete the boot process.
We need to know where these files are located, to find out boot up the liveDVD(USB) in "try ubuntu" mode to terminal>
post back the outputs - Between code Tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With that info we can give grub direction to boot, or perhaps obtain additional info. As the liveDVD has no problem booting, we can surmise that there is a issue within the install. We use the (C)ommand (L)ine (I)nterface because -> it is quicker, easier, and the more expedient in these instances. The CLI is the common denominator across all linux systems .

[INDENT]time and effort and we
[INDENT][INDENT][INDENT]get to the bottom of this
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-21
> **Bashing-om said:**
> bkocian; Hi ! Welcome to the forum;

```

sudo fdisk -lu
sudo parted -l
sudo blkid

```


Thanks for your help!  Here is the output from the commands above:

sudo fdisk -lu
```

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 14.9 GiB, 16013852672 bytes, 31277056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00045ca0

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 31277055 31275008 14.9G  c W95 FAT32 (LBA)

Disk /dev/sdb: 69.3 GiB, 74355769344 bytes, 145226112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x24122411

Device     Boot    Start       End  Sectors  Size Id Type
/dev/sdb1  *        2048  82749416 82747369 39.5G  7 HPFS/NTFS/exFAT
/dev/sdb2       82749438 145225727 62476290 29.8G  5 Extended
/dev/sdb5       82749440 145225727 62476288 29.8G 83 Linux

``` 

sudo parted -l
```

Model:  Patriot Memory (scsi)
Disk /dev/sda: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba


Model: ATA WDC WD740GD-00FL (scsi)
Disk /dev/sdb: 74.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  42.4GB  42.4GB  primary   ntfs         boot
 2      42.4GB  74.4GB  32.0GB  extended
 5      42.4GB  74.4GB  32.0GB  logical   ext4

```

sudo blkid
```

/dev/sda1: LABEL="UBUNTU 14_1" UUID="26A3-E19F" TYPE="vfat" PARTUUID="00045ca0-01" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="FA0C32D00C3287A1" TYPE="ntfs" PARTUUID="24122411-01" 
/dev/sdb5: UUID="527fb421-98cb-4a80-9152-5d08e46d83aa" TYPE="ext4" PARTUUID="24122411-05" 

```

formatting my whole hard drive is not a problem at all right now because I've already backed up all my data.  Your help is greatly appreciated :)

---

### Post by Bashing-om on 2015-03-21
bkocian; Well, so far so good.

Maybe not-so-good -> There is no provision for ubuntu's swap partition.
Maybe not a bad thing if you have the 8 Gigs of ram or more installed AND do not intend to hibernate.

IF you have the ram, and hibernation is not a factor we will continue, and see what results when grub (GRand Unified Bootloader) is for sure installed to the hard drive that ubuntu is installed to . Which I bet is the fault here. Bios is not able to pass off properly to the boot code.
Elsewise. Be much simpler and quicker just to (RE-)install ubuntu and this time make sure that the swap partition is created just a bit larger than the amount of ram installed on the computer.

If ya want we can use this as an occasion to learn and boot this install as is . It is your time and effort. One of our mandates here in the forum is to teach; I remain willing to assist.

we do
[INDENT][INDENT]as you decide
[/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-22
> **Bashing-om said:**
> bkocian; Well, so far so good.


Hi bashing-om,

I went ahead and reinstalled Ubuntu 14.10 and I chose "erase entire disk" so it formatted it and put a swap partition on there automatically.  Unfortunately I'm still getting a nearly identical error :(

[ATTACH=CONFIG]260832[/ATTACH]

any ideas?

Many thanks

---

### Post by Bashing-om on 2015-03-22
bkocian; Hey !

I see it as a different error " /dev/mapper/ubuntu--vg-root does not exist" .
Is there a real valid need to utilize the options to go with an encrypted system ? OR LVM ?
Unfortunately ( or fortunate for me ) I have no experience with encryption or LVM (Logical Volume Management ); Thus I do not know how to trouble shoot this situation.

May I suggest that you once more (RE-)install the operating system and this time do the default install - DO NOT choose 'LVM' nor encrypt any of the file system. A bit of a hassle, but, the only way I can be sure.

Then let's see what happens. 
"Disk /dev/sdb: 69.3 GiB" -> an SSD that was once a part of a "hybrid" hard drive system ? -> embedded raid data ?
Let's get the default system installed, a known foundation and if problems still persist we have a straight path to trouble shoot.

[INDENT][INDENT]them be my thoughts
[/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-22
> **Bashing-om said:**
> 
May I suggest that you once more (RE-)install the operating system and this time do the default install - DO NOT choose 'LVM' nor encrypt any of the file system.

Sorry about that, I just chose LVM just in case I wanted to change my partition sizes later.  I reinstalled again, this time choosing no LVM and I clicked the erase all bubble again.  Now the error seems to have greatly decreased in size but unfortunately it's not in plain English :(

The hdd is a SATA1 original 10k rpm raptor from many a year ago.  The mobo has an on-chip raid setup which is disabled.  All other OSes identify it as a normal hdd with no raid.


[ATTACH=CONFIG]260855[/ATTACH]

---

### Post by Bashing-om on 2015-03-23
bkocian; Much better.

OK, let's say that in that default install the installer is attempting to install grub to the 1st device it finds (sda). And what we need is grub installed to the drive that holds the ubuntu operating system. We can do this manually and direct where the boot code (grub) gets installed to.
We need a new look at what is, so we know the location of the ubuntu operating system.
From that liveUSB; post back the output of terminal command:
```

sudo fdisk -lu

```
and then from that liveUSB we install the boot code properly.

Sorry for all the hassle, it is no big deal .. just time consuming getting all the info.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-24
> **Bashing-om said:**
> bkocian; Much better.
From that liveUSB; post back the output of terminal command


Interesting, thanks for you help as always!

Here you go:

sudo fdisk -lu

```

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 14.9 GiB, 16013852672 bytes, 31277056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00045ca0

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 31277055 31275008 14.9G  c W95 FAT32 (LBA)

Disk /dev/sdb: 69.3 GiB, 74355769344 bytes, 145226112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbea72afa

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048 138938367 138936320 66.3G 83 Linux
/dev/sdb2       138940414 145225727   6285314    3G  5 Extended
/dev/sdb5       138940416 145225727   6285312    3G 82 Linux swap / Solaris

```

---

### Post by Bashing-om on 2015-03-24
bkocian; OK ;

From the liveUSB;
Terminal commands:
```

sudo fdisk -lu

```
to make sure that:
> 
/dev/sdb1  *         2048 138938367 138936320 66.3G 83 Linux

is still the same same ///
now install grub as per 'sdb1' still the target:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

OK grub installed, now reboot into the install; should boot normally to the GUI login screen.

[INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-24
> **Bashing-om said:**
> bkocian; OK ;
OK grub installed, now reboot into the install; should boot normally to the GUI login screen.


Ok I ran those commands but now the grub menu doesn't show up properly and throws me into a grub CLI.  It says something about BASH commands can be accepted and then has a text prompt like:
grub  >

Previously the grub menu worked fine on all my 14.10 installations but right after choosing ubuntu from the grub menu is when I got that exception emask error.

---

### Post by Bashing-om on 2015-03-24
bkocian; Hummm ...

Disappointing for sure, we dig deeper. 
There are 2 paths we can look down. But first, let's get a suspicion out of the way:
From the liveUSB - so that no other files systems are in use.
Let's make sure there is no embedded raid code on the hard drive. Will need to download the tool:
```

sudo apt-get install dmraid

```
Now remove any possible raid data:
```

sudo dmraid -E -r /dev/sdb

```

And now once more install grub to sdb:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

Reboot into the install, see what we have now.
And if that does not work, then we try and boot the system from grub > prompt OR rebuild grub's config  files.

I know how to do that
[INDENT][INDENT][INDENT]too
[/INDENT][/INDENT][/INDENT]

---

### Post by bkocian on 2015-03-25
> **Bashing-om said:**
> bkocian; Hummm ...
Now remove any possible raid data:
```

sudo dmraid -E -r /dev/sdb

```


ok I ran that command after installing dmraid (which is already installed by default on the liveUSB) but it said "no raid disks and with names: "/dev/sdb"

No nothing changed unfortunately.

i'm starting to think that since 14.04 worked fine but 14.10 does not, there must be some kind of hardware requirement that changed behind the scenes...

---

### Post by Bashing-om on 2015-03-26
bkocian; OK;

Then let us try the easier way to boot the crippled system, ( no I do not think a changed hardware requirement is at play here)
Remove the liveUSB and try and boot the install.
At the grub boot menu press the 'c' key for a command line:

I expect that the hard drive is now seen as the 1st device (sda -> hd0) - hd0 is 1st hard drive in grub speak.
to boot enter commands:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda ro
initrd (hd0,msdos1)/initrd.img
boot

```
If the configs files for grub are good, should boot. -If you boot here, we fix grub.
Else we may have to tell grub where it's config files are and have grub tell the kernel where it's initiating files are .
IF we find that the config files are corrupt, we then rebuild them.

[INDENT][INDENT]passing off,
[INDENT][INDENT][INDENT]one thing to another
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

