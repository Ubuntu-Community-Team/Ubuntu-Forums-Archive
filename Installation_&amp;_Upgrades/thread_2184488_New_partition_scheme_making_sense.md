---
title: "New partition scheme making sense?"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2013-10-29
Just installed. kubuntu 13.10 on my netbook.  I set it up with swap, then / partition, then /home partition.  Figured I'd do the smart thing this time since the lts doesn't work as well as newer versions on this machine.

Seems to work so far.  kubuntu-lowfat-settings doesn't seem to be available so I'll hafdisve to do that stuff manually.

When I do 

sudo fdisk -lu

I get:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00015d50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8007679     4002816   82  Linux swap / Solaris
/dev/sda2   *     8007680   125194239    58593280   83  Linux
/dev/sda3       125196286   625141759   249972737    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       125196288   625141759   249972736   83  Linux

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     7813119     3906552    b  W95 FAT32

```

I'm a little concerned about the "Partition 3 does not start on physical sector boundary." part, and I'm not sure this is set up the way I intended.

Any thoughts?

---

### Post by TheFu on 2013-10-29
fdisk code has been updated to support the newer AF HDD layouts, but it is hard to know if that has made it into any specific distro.
In the meantime, use **gparted** and **parted** to create partitions - by default, these tools will handle the alignment. Leave the alignment on MB ... I did cylinders and had to repartition later.  You also have a 4KB/sector HDD.

So ... that means a complete backup, repartition and restore is needed.  **fsarchive** can do the partition level backup with compression, but there are many other tools that do it well too - clonezilla, partimage, or any standard backup tool like rsync, rdiff-backup, duplicity ... the list goes on and on.

BTW, I did all this just a few weeks ago on my netbook ... went from 160G to 500G HDD.  After the fact, I wish that I'd known the automatic disk cloning tools didn't handle this stuff properly.

---

### Post by oldfred on 2013-10-29
You do not directly write into the extended partition, so that does not matter. What matters is every partition that you do write into starts at sectors that you can divide by 8. Or sda5 is the partition that matters.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by Rob Sayer on 2013-10-29
I'm afraid the above answers are not really clarifying this for me ...

So I should just reinstall and then use gparted to create a new /home partition, then move /home into it?

I should point out that I read every guide to doing this on install I could find that didn't assume you already know it alll already, and none of them include any of this stuff mentioned.

---

### Post by oldfred on 2013-10-29
All the recent versions of the Install and gparted create partitions correctly. 
Yours seem to be ok as sda5 is divisible by 8.

---

### Post by TheFu on 2013-10-29
> **Rob Sayer said:**
> I'm afraid the above answers are not really clarifying this for me ...

Whatever Oldfred says is correct. Seems you don't need to worry about "extended" partition alignments in the same way as for primary and logical partitions. Good to know - wish that I'd known that a few weeks ago. ;)

The information about **fdisk** stands ... for now. The specific version in your distro may or may not handle the alignment correctly.  **gparted** and **parted** ARE definitely safe and parted works enough like fdisk that there really isn't a learning curve.  fdisk doesn't handle GPT partitions correctly either.

**sudo parted -l**
gives the same output ... just a little more data than fdisk -l.  BTW, the cfdisk and sfdisk tools probably are tied to the fdisk version, so as long as the proper alignment and GPT partition data is a question, I'd avoid those tools too. At some point, it will all work out - don't know when that happens, but I haven't looked either.

---

### Post by SeijiSensei on 2013-10-29
If you might have multiple versions of Ubuntu on this machine, I'd consider setting up a common /boot partition as well.  I usually allocate 512 MB to that to avoid having the partition fill when there are frequent kernel updates.  Running "sudo apt-get autoremove" after the kernel is updated helps keep that process in check.  I put /boot first if there is no Windows partition, followed by swap, then extended.  I don't see any reason to use primary partitions for the standard Linux filesystem.  I format /boot with ext2 just to make things as simple as possible, too.

In the extended area I have partitions for each Ubuntu flavor (10 GB or so) and partitions for /usr/local (10 GB) and /home (all the rest) that I share across all the Linux versions.

---

### Post by fantab on 2013-10-30
> **Rob Sayer said:**
> I'm afraid the above answers are not really clarifying this for me ...

So I should just reinstall and then use gparted to create a new /home partition, then move /home into it?

I should point out that I read every guide to doing this on install I could find that didn't assume you already know it alll already, and none of them include any of this stuff mentioned.

> **oldfred said:**
> All the recent versions of the Install and gparted create partitions correctly. 
Yours seem to be ok as sda5 is divisible by 8.

It won't be a bad idea to run [FIXPARTS]("http://www.rodsbooks.com/fixparts/"), it might correct any anomaly with the Extended partition. However, as oldfred points out, your partition does look ok but for the message "[COLOR=#000000][FONT=Ubuntu Mono]Partition 3 does not start on physical sector boundary.[/FONT][/COLOR]"

---

### Post by Rob Sayer on 2013-10-30
OK, I haven't read any responses since my last post, but I tried a couple of things.  BTW this is single boot kubuntu.  I had deal linux/windows 7 but I yanked the windows pretty quickly.

First I just reinstalled without a separate /home partition and figured that later I'd try creating a new /home with gparted and migrating that folder.  But then I did sudo fdisk -lu and discovered that there was a "Partition [whatever, I didn't save the o/p] does not start on physical sector boundary" message for my big / partition.

So apparently the kubuntu installer didn't do any better than I did.  *Hmmmm* ...

Actually, I remember almost a year ago getting a similar message when it was dual boot win/12.04.  But frankly I was having so much trouble with the cedarview gpu drivers and broadcom 4727 wireless ... both of which seem to work quite nicely with the open source drivers now BTW ... I didn't pay much attention to it.

I think there's a high degree of probablility it's been running like this for some time now, and it's been plugging away, but I have to wonder if that has something to do with the fact that my external HDd date rates are about 1/2 what they are with my i3 based laptop ...

Anyway, I then reinstalled similarly to what I did originally (not the exact same part sizes exactly) and here's my:

sudo fdisk -lu

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000aed87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7999487     3998720   82  Linux swap / Solaris
/dev/sda2         8001534   625141759   308570113    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5         8001536   135999487    63998976   83  Linux
/dev/sda6       136001536   625141759   244570112   83  Linux

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     7813119     3906552    b  W95 FAT32
```

I'd prefer a 4Gb swap because I'll probablyt put a 2Gb ram board in this netbook and I'd like to have the hibernation capability.

At this point I'm getting sick of reinstalling.  If there's any problem with the above config, I'd prefer do dig into gparted if possible.  I wasn't impressed with the KDE partition editor at first glance.

---

### Post by fantab on 2013-10-30
If its a Linux ONLY Netbook then why do you need an Extended Partition in the first place? If I were you I'd use:
30GB Primary EXT4 Kubuntu /
4GB Primary SWAP
All the remaining GB Primary EXT4 [either /home or just plain DATA partition without any mountpoint]

There is a only 4 Primary Partition limit with 'msdos' partition table and if you are not going to use more than 4 Primary Partition then where is the need for an Extended Partition.

---

### Post by Rob Sayer on 2013-10-30
I don't know why there's an extended partition there ...

---

### Post by fantab on 2013-10-30
Are you auto managing the HDD with the Kubuntu installer?

---

### Post by Rob Sayer on 2013-10-30
I used manual partition with the kubuntu installer.

Swap first, then / bootable, then /home logical.

I have absolutely *no* idea why I have more partition types.  None whatsoever.  I did not specify any of that.

None of this appears in any install guides, and I rather wish people wouldn't try to make things look much more transparent than they actually are when they write those things.

---

### Post by fantab on 2013-10-30
If you're willing to re-install Kubuntu then I'd suggest that Delete all your Partitions using Gparted. Then Create a NEW partition table. Create Partitions as suggested earlier or according to your need (SWAP as first Partition is not a must). Then when installing Kubuntu choose 'Something Else' option to manually guide your install to your created parittions.

Like I said earlier you don't need Extended or Logical Partitions. If you choose Logical Partition then Extended will be created. 
EDIT: An Extended Partition is a Primary Partition which acts as  a container for Logical partiions.
You CAN have a maximum of FOUR Primary Partitions.

I have a asus netbook with Cedartrail. I use Fedora XFCE on it, except for 1080px HD videos everything works great. With the low RAM, I'd suggest you think about Xubuntu or Lubuntu.

Good Luck.

---

### Post by TheFu on 2013-10-30
> **Rob Sayer said:**
> I don't know why there's an extended partition there ...

Today, you don't need it, however, it really sucks when you need it (extended partition) and don't have one.  Better to have it and not need it, then to not have it and Neeeeeeeeeeeeeeed it, IMHO.

On MBR formated partitions, I always, always, always create a huge extended partition for everything except the main OS partition.  Being able to create a 10G logical partition to try out a new Linux version is nice.  Having already used up 4 primary partitions ... er ... sucks.

---

### Post by Rob Sayer on 2013-10-30
"If you choose Logical Partition then Extended will be created."

Again, no guides specify this.  I'm, again, a little tired of all the fake transparency and ease of use.

I might actually try the repartition and then reinstall as mentioned in post #14.  Gparted does not come with the kubuntu install live iso from what I could see.  I'm not so crazy about the kde one.  Does it do a decent job lining up sectors?

"With the low RAM, I'd suggest you think about Xubuntu or Lubuntu."

I had xubuntu on it once.  I prefer kubuntu.  It can be tweaked for speed ... although that would be a lot easier with 13.10 if kubuntu-lowfat-settings was in the repos at this point, I can do it manually  It doesn't take much more RAM, and it isn't much slower.  That, combined with the fact it's way more powerful, makes it just about as fast as xfce for me.

Edit:  Just found out there's no documentation for the kde partition editor on disk or on the doc site.  Not impressed.  This happens a lot.

---

### Post by Rob Sayer on 2013-10-30
This may help:

sudo lshw -class disk
```

  *-disk                  
       description: ATA Disk
       product: WDC WD3200BPVT-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXL1EA1YPKW6
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=000aed87
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 3815MiB (4GB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512

```

---

### Post by fantab on 2013-10-30
I don't use KDE, and never have so I don't know about KDE's disk management.
You can use [GPARTED Live]("http://gparted.sourceforge.net/livecd.php"). You may want to use [THIS TUTORIAL]("http://www.dedoimedo.com/computers/gparted.html") for Gparted, it may be a bit old but its relavent.

---

### Post by SeijiSensei on 2013-10-30
If Kubuntu is being installed by itself, why are you bothering with any of this?  Just use the default partitioning option, which repartitions the disk and sets up the organization Canonical thinks best.

If you want to have /boot, /, swap, and /home, then use all four available primary partitions.  Alternatively, set up the first three as primaries and tell fdisk to make the rest extended.  Then create the logical device for /home as /dev/sda5.

1. /boot (512 MB)
2. swap (4096 MB)
3. / (10-20 GB)
4. Extended
5.  /home (whatever part of extended you want to assign)

---

### Post by oldfred on 2013-10-30
If only Linux you can also use gpt which is the new partitioning for UEFI but will work with Ubuntu in BIOS mode. Then all partitions are primary. But do not use gpt if you ever thing you might want Windows as Windows only boots from gpt with UEFI.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

My old Windows is still on a separte MBR drive, but all my new Linux only drives are gpt and my BIOS boots with gpt drives just fine. Some may not.

 Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

### Post by Rob Sayer on 2013-10-30
I think I may have this done satisfactorily.

Gparted seems to allow 4096b alignment, but it doesn't come with the kubuntu install iso.

I read on a very knowledgeable blog post that the KDE partition manager will do this as well as of version 1.1.  The one that comes with kubuntu 13.10 is 1.0something and does not seem to have this capability that I can find.  Dang.

So I decided to just use the kde partition editor to create new partitions first from live USB and then check the properties to make sure the start sector is divisible by 8.  Since this may not work for the first partition, I made that swap again since it likely wouldn't matter for swap.  Even in a 1Gb RAM netbook I don't swap much.

After much fiddling, this is the layout I got:

```
~$ sudo fdisk -lu
```

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003b419

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065     8353799     4168867+  82  Linux swap / Solaris
Partition 1 does not start on physical sector boundary.
/dev/sda2   *     8353800   135733184    63689692+  83  Linux
/dev/sda3       135733248   625141759   244704256   83  Linux

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     7813119     3906552    b  W95 FAT32
```

No starting point error messages except for swap and no extra partitions this time.

I'm getting a little tired of doing this on this netbook (I had *way* more problems with 12.04), and unless someone sees something seriously wrong with this as set up I'm going to mark this [SOLVED] as long as doesn't freak out on me in a couple of days.

Thanks for all the responses.

---

### Post by oldfred on 2013-10-30
Almost every new install starts at sector 2048 and then partitions are on 1MB boundaries so they are divisible by 8. How did you get swap not to be divisible by 8?

---

### Post by Rob Sayer on 2013-10-31
I just put the slider for the swap partition as far to the left as possible in KDE partition manager.  That's what it gave me.  Is that going to cause a problem?

My data transfer speed from usb hd is double what it was before.  I was running it with a badly partitioned root from day one ... and that was linux or ubuntu that did that.  Not me.

As I said, I'm quite tired of dicking around on this machine ... it's an atom 2600/cedarview with a broadcom 4727 wireless, which was a nightmare in 12.04.  Those problems have been fixed in 13.04/13.10 but I just don't want to do this again unless there's going to be a serious problem with the way it's set up now.  I've never had any significant problems on the other machines I've put ubuntu on.

---

