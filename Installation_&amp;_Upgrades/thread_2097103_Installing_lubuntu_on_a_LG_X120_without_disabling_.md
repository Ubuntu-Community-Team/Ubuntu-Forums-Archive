---
title: "Installing lubuntu on a LG X120 without disabling smart on"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by snirk16 on 2012-12-22
hello

I received an 1600MHz atom netbook with 1024MB of RAM.
I tried lubuntu on a DoK and it seems to work fine out of the box.

I would like to install lubuntu on the hard drive but without risking the winXP and the SmartON (LG's quick boot option, based on splashtop). 

Is the preformence penalty when using wubi significant? its seems to me like the easiest option to install lubuntu without  messing  around with partitions.

  1. Are there any other ways to install lubuntu while ensuring both winXP and smartON unharmed?
  2. Is there another ubuntu variant you guys recommend for a net book? (leaner then lubuntu)

---

### Post by sudodus on 2012-12-22
Welcome to the Ubuntu Forums :-)

I think that it is a good idea to install Lubuntu. The question is ***how*** to do it.

Wubi is primarily for testing without touching the present installation, except that a big file is created, with the linux file system inside it. But such a file system is not as stable as an ordinary file system in a partition.

The wubi installation is fairly fast, that is not a problem, and you can test Lubuntu for a while. But when you really want to use it a lot and in the future let it be your main operating system, I suggest that you migrate your wubi install to a regular one.

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

When you edit the partitions in order to make room for a regular installation alongside Windows, a dual boot system, you should start by backing up your whole drive or at least make a rescue disk for Windows and backup your personal files, documents, pictures etc. It is usually safe, and nothing happens to Windows, but things can go wrong, the risk is not zero.

I don't  know anything about SmartON.

---

### Post by snirk16 on 2012-12-22
Thank you,

Actually I'm returning to ubuntu after a few years.
So a proper install it is...

The smartON is basically a small linux disro. which boots up very fast (few seconds) and lets you conncet to the web, play to music/videos and so on.
Its a nice function I'd like to keep.

I have three partitions:
[LIST=1]
[*]Recovery 4.3GB (don't think its smartON)
[*]~50GB winXP
[*]~100GB user data
[/LIST]

What will be the best strategy to re-partition the drive?

---

### Post by sudodus on 2012-12-22
So welcome back to ubuntu :-)

SmartON sits somewhere. Can you find out where? Does it have a grub or lilo boot system? Is it inside Windows's file system (like Wubi)?

You tried lubuntu on a DoK and it seems to work fine out of the box. Is that a USB flash drive? Please boot like that again and run the following terminal commands
```
sudo fdisk -lu
```
Mount your partitions (for example using the file browser) and run
```
df
```
and post the output in a reply. It will make it easier to give good advice.

Without that information I would suggest that you take part of your data partition, at least 8 GB, but I suggest around 20 GB for Lubuntu. This can be done with ***gparted*** (included in the live Lubuntu CD/USB system).

Make a swap partition of the same size as (or a little bigger than) the RAM, say 1280 MB. The rest of the freed space can be used for the linux root partition /.

But before you start with any partitioning:
1. Try to find where SmartON is stored!
2. ***Backup*** your drive or at least you should make a recovery disk for Windows and backup your personal data.

---

### Post by snirk16 on 2012-12-22
smartON sits in the winXP partition, I found it there in an hidden directory. 
Don't know about lilo/grub, but I don't think there is. I believe its being booted in the bios/MB level - with a dedicated physical button.

Of course I'll back up everything! I'm not worried about the data, I'm only worried about loosing usability (XP, smartON, recovery partition, etc.)

BRB with the terminal output you asked

---

### Post by snirk16 on 2012-12-22
here are the terminal outputs you asked for:
```
Filesystem     1K-blocks     Used Available Use% Mounted on
/cow              507864    36240    471624   8% /
udev              499280        4    499276   1% /dev
tmpfs             203148      804    202344   1% /run
/dev/sdb          983792   732624    251168  75% /cdrom
/dev/loop0        653952   653952         0 100% /rofs
tmpfs             507864        4    507860   1% /tmp
none                5120        0      5120   0% /run/lock
none              507864      132    507732   1% /run/shm
none              102400       12    102388   1% /run/user
/dev/sda1        4194300  2574328   1619972  62% /media/lubuntu/RECOVERY
/dev/sda2       52428796 28802028  23626768  55% /media/lubuntu/FA9E21799E213015
/dev/sda3       99664892  2451824  97213068   3% /media/lubuntu/184C25284C25025C

```

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce7d3b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   12  Compaq diagnostics
/dev/sda2   *     8390656   113248255    52428800    7  HPFS/NTFS/exFAT
/dev/sda3       113248256   312578047    99664896    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1007 MB, 1007681536 bytes
31 heads, 62 sectors/track, 1024 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366752  3470046675   123339962   f4  SpeedStor
/dev/sdb2   ?   378192737   710426324   166116794   10  OPUS
/dev/sdb3   ?   225603442   225603451           5   74  Unknown

Partition table entries are not in disk order

```

---

### Post by sudodus on 2012-12-22
> **snirk16 said:**
> here are the terminal outputs you asked for:
```
Filesystem     1K-blocks     Used Available Use% Mounted on
...
/dev/sda1        4194300  2574328   1619972  62% /media/lubuntu/RECOVERY
/dev/sda2       52428796 28802028  23626768  55% /media/lubuntu/FA9E21799E213015
/dev/sda3       99664892  2451824  97213068   3% /media/lubuntu/184C25284C25025C

```

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce7d3b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   12  Compaq diagnostics
/dev/sda2   *     8390656   113248255    52428800    7  HPFS/NTFS/exFAT
/dev/sda3       113248256   312578047    99664896    7  HPFS/NTFS/exFAT
...

```
This looks good.

- Only 3 primary partitions, which means that you can make an extended partition without deleting any of the existing ones.

- An almost empty data partition, that you can shrink and make space for Lubuntu. So you can get 20GB or even 30GB for Lubuntu. Sometimes it is good to have some extra space on the root partition, for example when large temporary files are created.

Many people recommend that you use Windows's own tool to shrink an NTFS partition. It works well also with gparted, but maybe it is safer to treat Microsoft stuff with Microsoft tools, and then, when there is free space, start using gparted from the Lubuntu install drive.

So create an extended partition of the free space. Inside the extended partition, create a swap partition of 1280 MB or 2 GB (depending on your habits to fill memory). And use the rest for an ext4 partition, which should be used as the root file system of Lubuntu.

Finally start the installation and at the partitioning page, select 'Something else' and use the ext4 partition for the root file system. It will find the swap partition automatically, and also find automatically where to put grub (into the mbr area of the only HDD of the netboot).

Good luck :-)

---

### Post by oldfred on 2012-12-22
I know nothing about Smart-on. But all BIOS based computers boot from BIOS to MBR which then loads more boot code from where ever MBR sends it.
Your Smart-on may be a customized BIOS. It is easy to reinstall a standard Windows boot loader but if your BIOS is customized then you may want to back that up separately just to be safe.

normally I consider it easier just to reinstall grub or a Windows boot loader but use this to back up MBR.
       Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

    
Then mbr.bin is a copy of you MBR.

---

### Post by snirk16 on 2012-12-24
> **sudodus said:**
> This looks good.

- Only 3 primary partitions, which means that you can make an extended partition without deleting any of the existing ones.

- An almost empty data partition, that you can shrink and make space for Lubuntu. So you can get 20GB or even 30GB for Lubuntu. Sometimes it is good to have some extra space on the root partition, for example when large temporary files are created.

Many people recommend that you use Windows's own tool to shrink an NTFS partition. It works well also with gparted, but maybe it is safer to treat Microsoft stuff with Microsoft tools, and then, when there is free space, start using gparted from the Lubuntu install drive.

So create an extended partition of the free space. Inside the extended partition, create a swap partition of 1280 MB or 2 GB (depending on your habits to fill memory). And use the rest for an ext4 partition, which should be used as the root file system of Lubuntu.

Finally start the installation and at the partitioning page, select 'Something else' and use the ext4 partition for the root file system. It will find the swap partition automatically, and also find automatically where to put grub (into the mbr area of the only HDD of the netboot).

Good luck :-)

Everything is backed up (thanks for the MBR backup tip, oldfred) and I'm ready to partition.
Let me just make sure I got it right. 
In the end state there are 5 partitions:
recovery
winXP
shrinked ntfs data
linux swap
ext4 for lubuntu

Or the data partition is being devided to swap and ext4 partitions? (recovery, winXP, swap+ext4 inside the old NTFS data partition)

as you can see I don't no much about partitioning...

---

### Post by oldfred on 2012-12-24
LInux has to use Linux formatted partition, and does not work from Windows formats (except wubi).
You will also see an extended partition. MBR(msdos) partitioning only allows 4 primary partitions. But one primary can become an extended which is just a container for many logical partitions.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
            GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

 Error in below - you cannot make /home NTFS and should not share /home with other installs. Use another NTFS data partition if sharing data with Windows.
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

### Post by snirk16 on 2012-12-25
Thanks a lot guy!

I decided to split the large data partition to swap an ext4.
WinXP and SmartON are working fine and so is Lubunto.

---

### Post by oldfred on 2012-12-25
Glad you got it working. :)

---

### Post by sudodus on 2012-12-26
Congratulations to a good job snirk16 :-)

---

