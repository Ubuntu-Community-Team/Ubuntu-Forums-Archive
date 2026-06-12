---
title: "Dual booting on an SSD"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by hellfeuer on 2010-11-17
I'll be getting a new laptop with an 80GB SSD. It comes with Windows 7 installed. I want to dual boot with Maverick, and I have some questions about partition alignment.

Normally when I install Ubuntu, I shrink the Windows partition using Windows' built in tool (I forgot what its called). In this case, can I use it to ensure that my Windows partition is aligned properly? Is this simply a question of shrinking to a size that is a multiple of the erase block size? If not, can I use Gparted/fdisk to do this while installing Ubuntu? I don't want to have to reinstall Windows, but I would like both Windows and Ubuntu partitions to be aligned properly.

I know there are many threads about partitioning but I couldn't find a thread that addressed this issue specifically.

---

### Post by oldfred on 2010-11-17
Some info:


SSD info
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment#post373226)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by hellfeuer on 2010-11-17
Thanks but that doesn't answer my question. I'm not looking for SSD optimization tips for Ubuntu in general. I've already found those. All I want to know is how to align my Windows partition correctly when installing Ubuntu, without having to reinstall Windows.

---

### Post by Herman on 2010-11-17
If your Windows partition is already aligned correctly, (or eve if it isn't), the Ubuntu installer's partitioner won't 'move' it on you, so you don't need to worry about that.
The standalone GParted, which is also found in the Live CD, is the one which needs care not to 'move' the entire Windows partition, but that can easily be prevented by simply removing the 'align to cylinder boundaries' from the checkbox before commiting to the resize operation. Since we're in an SSD, there are no cylinders and we want to align to the erase block size instead, 1 KB should work for most flash memory. I don't think CHS addressing is used anymore anyway, LBA has well and truly taken over by now, even for hard disk drives.

I don't know anything about resizing with Windows 7 or Vista's own 'Disk Manager', I tried it once and it worked alright when I tried it, but I have been using GParted and the Ubuntu installer's partition editor for years and never had any problems with them yet, so I don't see why I should change now. I don't mind if others use Windows own tools though, you can if you want, it doesn't bother me. I don't know if it will shift your partition alignment or not, ask in a Windows forum maybe?

I also highly recommend thorough file system checking both before and  after resizing any partition, especially if it contains an NTFS file  system. (CHKDSK /R two or three times before or until no more problems are found and once afterwards).

Just make sure you make a backup as you would always do anyway before using any partition editing software.

I'm not sure about how to get a non-first partition in the correct alignment. I'll think that over for a while, meantime maybe somebody else has an idea.

---

### Post by hellfeuer on 2010-11-28
So if I understand correctly, when installing Ubuntu if I'm resizing the windows partition with GParted all I have to do is ensure that its length 'correct'? Then what about the Ubuntu partition itself? Just start and end it on multiples of the erase block size?

---

### Post by Herman on 2010-11-28
It's supposed to be advantageous to have the start point of partitions in an SSD drive or any other kind of flash memory aligned with an erase block boundary, but the ends of the partitions don't matter.

The size of the erase blocks may vary between different manufacturers and even various products made by the same manufacturer, so the best idea is to consult your SSD manufacturer and know your make and model number.

It's reasonably well know that a likely start point for the first partition could be at the 1 MiB or sector 2048 and that should generally work out right for most kinds of flash.

Your question about how to find the optimal start point for a non-first partition is a good one.
The new versions of GParted, feature an 'align to MiB' option which replaces the checkboxes the older version had for 'align to cylinder boundaries'. I have tested it a little, and it seems to work okay for me. Try with Maverick Meerkat's GParted or get yourself the latest version of GParted by downloading a recent version of Parted Magic or GParted Live CD. Those are up to version 7 now, and I think Mavericks is 5.1, but still better than Lucid's GParted.

If you're after a more technical answer try this link, [http://thunk.org/tytso/blog/category/computers/ssd/](http://thunk.org/tytso/blog/category/computers/ssd/) it's over a year old, so I'm not sure if the improvements to GParted supercede this or not. Look especially under '**[Aligning filesystems to an SSD&#8217;s erase block size]("http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/")**' Given that information if you're keen enough and have enough technical and mathematical ability, you might be able to compute the optimal start point yourself, otherwise just leave it up to GParted and hope for the best.

---

### Post by Herman on 2010-11-29
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
[COLOR=Red]**32 heads, 32 sectors/track**[/COLOR], 122114 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c6990b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        [COLOR=Red]**1024**[/COLOR]   125044735    62521856   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f5f77f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        **2048**      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2          206848   625141759   312467456    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00080d93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1547300474   773650206   83  Linux
/dev/sdc2      1750346010  1953520064   101587027+  83  Linux
/dev/sdc3      1547300475  1750346009   101522767+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 514 MB, 514850816 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a372

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63      996029      497983+  83  Linux

```The output from the 'sudo fdisk -lu' command shown above shows that I have changed my SSD drives number of heads and cylinders as recommended for my particular make and model of SSD drive. This information is available in my SSD manufacturer's web forums along with other hints and recommendations.
My SSD drive only has Ubuntu in it, and it starts in sector 1024, as you can see from the fdisk output. I used a swap file instead of a swap area so it only has one partition.

The second drive is a regular HDD and contains a trial installation of Windows 7 which has its boot partition starting in sector 2048, as shown in the fdisk output.

The other two drives are a 1000 GB data drive and a 512 mg USB flash memory stick with bog standard partition alignment, (starting in sector 63).

---

### Post by Herman on 2010-11-29
If your laptop comes with Windows already installed in it the MBR will already be set up to suit Windows and I don't think you can change it unless you're prepared to delete Windows and re-install, you'll just have to live with it.
Don't worry, it'll still be plenty fast enough, just let GParted align it to MiB I think, and that will be fine.

---

### Post by hellfeuer on 2010-11-30
Thanks a lot. My laptop's arrived so I'll try it out and tell you how it goes.

---

