---
title: "Setting up FakeRAID on an existing system"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by jrobot on 2010-08-12
I have 2 750GB harddrives with multiple NTFS and ext3 partitions and have just added two empty 1.5TB drives (with WD Advanced Format Technology) to the computer. I have several external drives of various capacities for temporary data storage. My final objective is to have two mirrored RAID arrays that I can access with both Ubuntu 10.04 and Windows Vista (which I still need for applications that aren't supported by WINE), and I'm trying to find out how to do this.

At the moment, the 1.5TB disks are mirrored in the BIOS settings, and I was able to add a blank NTFS partition to the array using GParted. However, I am now unable to mount any of my partitions (other than the Ubuntu one) and cannot use GParted to copy a partition to the RAID array (I get a generic resource in use message, but I have no other applications open and am opening GParted after a fresh boot).

My Ubuntu install is heavily customized, so I would prefer not to reinstall it if at all possible. If it matters, the OS was not installed as 10.04, but was updated incrementally over time, starting at Hardy Heron.
I initially did an apt-get install of dmraid and kpartx after reading [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) and [http://superuser.com/questions/168195/gparted-wont-detect-raid-0-in-ubuntu-lucid-lynx](http://superuser.com/questions/168195/gparted-wont-detect-raid-0-in-ubuntu-lucid-lynx).

For some reason, my 750GB drives are recognized as belonging to a broken RAID array even though they are not set up that way in BIOS.

HD configuration:

sda: (I cannot mount any of these partitions :()
1: ext3 (Debian Installation)
2: ntfs (Vista Installation)
3: ntfs (Data)

sdb:
1: ext3 (Ubuntu, mounted at /)
2: linux-swap
3: ntfs (Data, I can no longer mount this for some reason :confused:)

sdc:
1MiB unformatted (read something about needing to do this with Advanced Format Tech)
1: ntfs (I created this because I need to reinstall Vista - still haven't managed to install service pack 2)
unformatted

sdd: (see sdc)

```

$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 59 2010-08-12 14:09 control
brw-rw---- 1 root disk 252,  0 2010-08-12 14:09 isw_cabhdadfaa_LargeRAID
brw-rw---- 1 root disk 252,  1 2010-08-12 14:09 isw_cabhdadfaa_LargeRAID1

```

```

$ sudo dmraid -r
/dev/sdd: isw, "isw_cabhdadfaa", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdc: isw, "isw_cabhdadfaa", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sda: isw, "isw_geghiffch", GROUP, ok, 1465147053 sectors, data@ 0

```

```

$ sudo dmraid -tay
ERROR: isw: wrong number of devices in RAID set "isw_geghiffch_750GB HardDrive" [1/2] on /dev/sda
isw_cabhdadfaa_LargeRAID: 0 2930272520 mirror core 2 131072 nosync 2 /dev/sdc 0 /dev/sdd 0 1 handle_errors
ERROR: creating degraded mirror mapping for "isw_geghiffch_750GB HardDrive"
isw_geghiffch_750GB HardDrive: 0 1465141512 linear /dev/sda 0
isw_cabhdadfaa_LargeRAID1: 0 251658240 linear /dev/mapper/isw_cabhdadfaa_LargeRAID 2048

```

Odd, I just ran this again and got:
```

$ sudo dmraid -tay
ERROR: isw: wrong number of devices in RAID set "isw_geghiffch_750GB HardDrive" [1/2] on /dev/sda
isw_cabhdadfaa_LargeRAID: 0 2930272520 mirror core 2 131072 nosync 2 /dev/sdc 0 /dev/sdd 0 1 handle_errors
ERROR: creating degraded mirror mapping for "isw_geghiffch_750GB HardDrive"
isw_geghiffch_750GB HardDrive: 0 1465141512 linear /dev/sda 0
ERROR: dos: partition address past end of RAID device
isw_cabhdadfaa_LargeRAID1: 0 251658240 linear /dev/mapper/isw_cabhdadfaa_LargeRAID 2048
isw_geghiffch_750GB HardDrive1: 0 156248127 linear /dev/mapper/isw_geghiffch_750GB HardDrive 63
isw_geghiffch_750GB HardDrive2: 0 167772160 linear /dev/mapper/isw_geghiffch_750GB HardDrive 156250112

```

I don't know if it is intended this way, but GParted has 6 entries: one each for sda-d and one for each HD pair. 

Thanks in advance.

---

### Post by jrobot on 2010-08-16
bump.

I went ahead and installed Ubuntu from scratch after setting up the two RAID arrays. I transferred my old Ubuntu install to a new partition, and it is now able to mount partitions properly. Odd.

My problem now is that every time I shut down my computer, the second disk of the RAID array "SmallRAID" goes offline and GRUB2 is not found. There are no problems if I simply reboot, and this happens regardless of whether I shut down from within Ubuntu or Windows Vista.

I can restore the drive to being online by running "sudo dmraid -ay". Strangely, the results are:

```

$ sudo dmraid -ay
RAID set "isw_ccgbgiigfe_LargeRAID" already active
RAID set "isw_jdifdfaee_SmallRAID" already active
RAID set "isw_ccgbgiigfe_LargeRAID1" already active
RAID set "isw_ccgbgiigfe_LargeRAID2" already active
RAID set "isw_ccgbgiigfe_LargeRAID3" already active
RAID set "isw_jdifdfaee_SmallRAID1" already active
RAID set "isw_jdifdfaee_SmallRAID2" already active
RAID set "isw_jdifdfaee_SmallRAID3" already active
RAID set "isw_jdifdfaee_SmallRAID4" already active

```

When I run the command with the -t flag, I get:
```

$ sudo dmraid -tay
isw_ccgbgiigfe_LargeRAID: 0 2930272520 mirror core 2 131072 nosync 2 /dev/sdc 0 /dev/sdd 0 1 handle_errors
isw_jdifdfaee_SmallRAID: 0 1465141512 mirror core 2 131072 nosync 2 /dev/sda 0 /dev/sdb 0 1 handle_errors
isw_ccgbgiigfe_LargeRAID1: 0 2048000000 linear /dev/mapper/isw_ccgbgiigfe_LargeRAID 2048
isw_ccgbgiigfe_LargeRAID2: 0 156272641 linear /dev/mapper/isw_ccgbgiigfe_LargeRAID 2773989376
isw_ccgbgiigfe_LargeRAID3: 0 167792640 linear /dev/mapper/isw_ccgbgiigfe_LargeRAID 2606196736
isw_jdifdfaee_SmallRAID1: 0 419428352 linear /dev/mapper/isw_jdifdfaee_SmallRAID 2048
isw_jdifdfaee_SmallRAID2: 0 760498176 linear /dev/mapper/isw_jdifdfaee_SmallRAID 419430400
isw_jdifdfaee_SmallRAID3: 0 33552384 linear /dev/mapper/isw_jdifdfaee_SmallRAID 1179928576
isw_jdifdfaee_SmallRAID4: 0 251637761 linear /dev/mapper/isw_jdifdfaee_SmallRAID 1213480960

```

I should note that neither of the disks in the array "LargeRAID" ever goes offline, only the second disk in "SmallRAID"

Before I updated my BIOS to the newest version, both of the drives in "SmallRAID" went offline when I shut down.

GRUB is on "SmallRAID" and "LargeRAID" contains data. 

What's going on?

---

### Post by NHclimber on 2010-08-19
FakeRAID (dm-raid45) is/has been in flux over the last year.

upstream gparted was literally just fixed (see [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/600729](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/600729))

Although it is not possible to partition or format as part of the *install* of either lucid or maverick, it is possible to partition and format from 9.10 and then install to that.

As far as your newer trouble, you should file a bug ('ubuntu-bug linux-image') so that someone can help you track down if it's bios or dying drive or something else.

---

### Post by jrobot on 2010-08-24
Thanks for the reply, NHclimber. After wasting days trying to get this worked out, I deleted the OS RAID array, formatted sdb, and recovered the partition table of sda. sdb is now used as a backup drive with disk images created with partimage. Can you suggest a better solution? The program is no longer being actively developed, and it does not fully support NTFS. Furthermore, compiling it was really annoying because of old dependencies.

> Although it is not possible to partition or format as part of the *install* of either lucid or maverick, it is possible to partition and format from 9.10 and then install to that.

I was able to use the Lucid install CD to partition the FakeRAID array by creating a symlink (the installer renamed the drives, as indicated in the bug report you linked to).

I performed a low-level scan of sdb with SpinRite and found no problems.

What I have noticed is that gparted appears to have recently run into problems with copying and pasting partitions - it reports that the destination partition is too small unless it is resized to be larger than the source. This makes the program useless for copying partitions with filesystems that are not supported well enough to be resized.

I can't provide any more information at the moment because my computer is currently in transit in a semi-dissassembled state.

---

