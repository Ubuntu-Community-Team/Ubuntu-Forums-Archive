---
title: "Linux Not Fully Prepared for 4096-Byte Sector Hard Drives"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-02-14
[Linux Not Fully Prepared for 4096-Byte Sector Hard Drives](http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives)
[Slashdot: Linux Not Quite Ready For New 4K-Sector Drives](http://hardware.slashdot.org/story/10/02/14/1541244/Linux-Not-Quite-Ready-For-New-4K-Sector-Drives?art_pos=9) - has soem solutions.

Does Lucid already have solution to this?
Will it be solved in time for Lucid? Lucid will be LTS so I hope it will be better supported, because in 2 years I'm pretty sure most HD would be 4k sector.

I have one of these drives arriving this week and am wondering what to do. For now it will be a storage drive in external enclosure, so not sure what filesystem to use. Sadly I think I will have to keep it compatible with windows so ntfs might have to be used (my winxp install never recognized ubuntu partitions).

According to article ubuntu parted has option, but I doubt many people know to use it, they'd have to research it.

---

### Post by VMC on 2010-02-14
The problem as I see it is the kernel can handle 4k sector sizes, what it can't handle is the drives are saying its 512 byte to satisfy XP's. Refer to [this]("http://hardware.slashdot.org/comments.pl?sid=1549602&cid=31135754") an other comments

---

### Post by ronacc on 2010-02-14
interesting , I'll keep it in mind while I shop for a new drive to replace one that failed yesterday .

---

### Post by MacUntu on 2010-02-15
> **VMC said:**
> The problem as I see it is the kernel can handle 4k sector sizes, what it can't handle is the drives are saying its 512 byte to satisfy XP's. Refer to [this]("http://hardware.slashdot.org/comments.pl?sid=1549602&cid=31135754") an other comments

AFAIK there are also drives that don't "lie" about the sector size in use - very confusing.

---

### Post by Reiger on 2010-02-15
Linux can't handle intentionally broken kit. Oh, noes... 

Seriously though: drives announce their ID to the kernel and I imagine we will see a work-around layer for them based on ID detection; if the kernel developers think its worth their time.

---

### Post by antiram on 2010-02-15
for the drives with physical sector size != logical sector size:
use "fdisk -u" to set the unit from cylinders to sectors. Then make new partition and set the first sector to 64 or any other aligned. Then set the size eg. to +20G for a 20GB partition.

i read somewhere, that a fresh karmic installation (with new partiton table or so) use a 128k alignment as default.

there are also some interesting variables eg. for /dev/sda
/sys/block/sda/queue/hw_sector_size
/sys/block/sda/queue/logical_block_size
/sys/block/sda/queue/physical_block_size
(from a .33 kernel, don't know if .32 has it)

---

### Post by blazemore on 2010-02-15
Hands up who has a 4k sector-ed drive.

---

### Post by andrewabc on 2010-02-15
> **blazemore said:**
> Hands up who has a 4k sector-ed drive.

I just got my 1tb today.

I've read over slashdot etc, and I stil have no idea how to properly format it.

I created msdos partition table (I had no idea which partition table to choose from).

Now I am about to create a partition using entire drive. But there are no options in gparted to select where to start partition. I'm supposed to start at 64 instead of 63, gparted is saying it is a 63 drive, and no idea where to input options.
It also is not allowing me to choose NTFS. I want this to be compatible with winxp. winxp not going to be installed to it now, but I might want to view data from winxp installed on other hard drive.

Help!

I'm using ubuntu 9.10

sudo fdisk -l
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7720    62010868+  83  Linux
/dev/sda2            7721        7783      506047+   5  Extended
/dev/sda5            7721        7783      506016   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x221b01b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1019     8185086   12  Compaq diagnostics
/dev/sdb2   *        1020        7450    51657007+   7  HPFS/NTFS
/dev/sdb3            7451       38913   252726547+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005c44f


```

No wonder people are confused. I have no idea if using 9.10 gparted defaults work with this 4k drive. Or how to select what options to use using gparted.

---

### Post by SeePU on 2010-02-15
I am considering doing the same as you.  Did WD lie about other operating systems not needing any configuration for the formatting and alignment of partitions?

If you are using NTFS so that Windows can access the drive, you can format it with Windows 7 or use the WD Alignment Utility.

I was hoping you could just use GParted but it sounds like you have to use fdisk if you don't want to use NTFS.

> for the drives with physical sector size != logical sector size:
use "fdisk -u" to set the unit from cylinders to sectors. Then make new partition and set the first sector to 64 or any other aligned. Then set the size eg. to +20G for a 20GB partition.  Try the above?

---

### Post by andrewabc on 2010-02-15
I'm not familiar with fdisk
So I'm not sure what to type fdisk -u  (Do I need to put sdc after that to make sure it selects my 1tb and not 320gb HD or 60gb ssd?)

Yes WD did lie, because they want to make sure winxp is supported, which doesn't support 4k drives. So hard drive tells OS it is 512byte. Although for some reason vista/win7 see past this lie and linux doesn't yet(?).

I only have winxp/ubuntu. No win7.

---

### Post by VMC on 2010-02-15
> **andrewabc said:**
> I'm not familiar with fdisk
So I'm not sure what to type fdisk -u  (Do I need to put sdc after that to make sure it selects my 1tb and not 430gb HD or 60gb ssd?)

Yes WD did lie, because they want to make sure winxp is supported, which doesn't support 4k drives. So hard drive tells OS it is 512byte. Although for some reason vista/win7 see past this lie and linux doesn't yet(?).

I only have winxp/ubuntu. No win7.

```
fdisk -u /dev/sdc
```

Then push "m" to see other options.

---

### Post by andrewabc on 2010-02-15
ok.

> andrew@andrew-desktop:~$ sudo fdisk -u /dev/sdc

The number of cylinders for this disk is set to 121601.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)


And now
> Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-1953525167, default 63): 64 
Last sector, +sectors or +size{K,M,G} (64-1953525167, default 1953525167): 


I'm confused what to put in now. just 1953525167 ? Or 995g for a 995gb partition leaving ~5 gb unpartitioned space? I'm not sure how many gb I can put in.

---

### Post by VMC on 2010-02-15
> **andrewabc said:**
> ok.



And now


I'm confused what to put in now. just 1953525167 ? Or 995g for a 995gb partition leaving ~5 gb unpartitioned space? I'm not sure how many gb I can put in.

You can just play around with it and later change it. There's nothing in there anyway. It can't hurt anything. I'm curious thought why you started at 64 instead of 63.

Also I get that first message on my "normal" 250 GB sata hard drive.

---

### Post by SeePU on 2010-02-15
> **andrewabc said:**
> I'm not familiar with fdisk
So I'm not sure what to type fdisk -u  (Do I need to put sdc after that to make sure it selects my 1tb and not 320gb HD or 60gb ssd?)
I only have winxp/ubuntu. No win7.Yes, I assume you need the device syntax added to fdisk -u.  I've never done it that way before, though.

If you don't have Windows 7 (I don't either), you can use the WD tool - if you want to format NTFS.  

[http://www.wdc.com/en/products/advancedformat/](http://www.wdc.com/en/products/advancedformat/)

Notice they state you don't need it if you use a non-Windows OS.  That's what I mean by them lying.  It appears they didn't research it enough or/and they know they won't be supporting what you need to do with other operating systems if you know what I mean.  AKA, they only address Windoze.

---

### Post by andrewabc on 2010-02-15
I thought 64 was needed to have 4k sectors? So it would be aligned properly and not have huge slowdown.

It starting at 63 was the problem everyone was having I thought. And it's supposed to start at 64 (or multiples of 32?) to work properly.

I went with
> First sector (63-1953525167, default 63): 64 
Last sector, +sectors or +size{K,M,G} (64-1953525167, default 1953525167): 1900000000

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
andrew@andrew-desktop:~$ 


sigh.
gparted sees filesystem, but there is no format.
Can I now use gparted to format to a filesystem? It still won't let me select ntfs. Only ext/fat/swap are available.

---

### Post by SeePU on 2010-02-15
Thanks for replying to this thread, VMC!!! :)

I want to get to the bottom of this, too, as I might buy one of these drives myself.  

I need to read more about it but as it is an alignment problem, I wonder if the designers of gparted will eventually address this issue and make changes accordingly?

---

### Post by andrewabc on 2010-02-15
I got impatient and formatted to ext4.
All appears to be normal.

[[IMG]http://img534.imageshack.us/img534/6534/screenshotapplyingpendi.png[/IMG]](http://img534.imageshack.us/i/screenshotapplyingpendi.png/)

Still wondering why only ext/fat/swap can be applied.

Also wondering why it is reporting 2% (14.41gb) used.

ARGH! I can open it, but for whatever reason I can not write files to it? I can't create folder, or paste files... When I originally click on the drive to open it it asks for my password. I give it and it opens. I double click on lost and found and it says I don't have permission to view the files in that folder. I tried adding myself to certain groups and stuff. no luck.

wtf now 45gb is used and I didn't put anything on it?
[[IMG]http://img713.imageshack.us/img713/1779/screenshot6bedd91107c14kn.png[/IMG]](http://img713.imageshack.us/i/screenshot6bedd91107c14kn.png/)

I labelled drive "green"
[[IMG]http://img163.imageshack.us/img163/4397/screenshotgreenproperti.png[/IMG]](http://img163.imageshack.us/i/screenshotgreenproperti.png/)

Why can't I put files on the disk!? I'm guessing I have to change persmission to allow groups and others to create/delete files? How do I get into root to change the settings from that area?
EDIT:
Ok figured out a way by using [this](http://www.ahinc.com/linux101/permission.htm#chown)
> sudo chown andrew /media/green
Backing up files/folders to drive now. Says I'm getting 47mb/s (now 41) speed.

---

### Post by SeePU on 2010-02-15
Correct me if I am wrong but these may be options:
1) NTFS - WD Alignment tool, Windows 7 partition mgr, fdisk -u etc.

Perhaps, this too?:
mkntfs -c and set number of clusters to 4096 if they aren't already.   Then see if you can use gparted to set the beginning and ending of each sector to be...????   

That is the part I am trying to figure out. 

Anyone else think this is annoying?

---

### Post by andrewabc on 2010-02-15
> **SeePU said:**
> Correct me if I am wrong but these may be options:
1) NTFS - WD Alignment tool, Windows 7 partition mgr, fdisk -u etc.

Perhaps, this too?:
mkntfs -c and set number of clusters to 4096 if they aren't already.   Then see if you can use gparted to set the beginning and ending of each sector to be...????   

That is the part I am trying to figure out. 

Anyone else think this is annoying?

I've always been able to make ntfs partitions on my old hard drive using gparted. Not sure why not able to easily do so on my new hard drive. Must be a setting somewhere when I made the partitions. I thought I made msdos, and though most compatible with windows...

---

### Post by VMC on 2010-02-15
Look into ntfs-3g. Gparted uses that. For the longest time ntfs-3g was in beta. You can read up on 'man ntfs-3g'. 

Also, maybe visit [http://ntfs-3g.org](http://ntfs-3g.org). They have a support forum. Maybe ask questions there.

Edit: ok found this info. [Why is the driver slow?]("http://www.tuxera.com/community/ntfs-3g-faq/"). Go there and search for "4096". Lots of info.

Some more info [here]("http://www.tuxera.com/forum/viewtopic.php?f=3&t=124").

---

### Post by andrewabc on 2010-02-15
> **VMC said:**
> Look into ntfs-3g. Gparted uses that. For the longest time ntfs-3g was in beta. You can read up on 'man ntfs-3g'. 

Also, maybe visit [http://ntfs-3g.org](http://ntfs-3g.org). They have a support forum. Maybe ask questions there.

Edit: ok found this info. [Why is the driver slow?]("http://www.tuxera.com/community/ntfs-3g-faq/"). Go there and search for "4096". Lots of info.

Some more info [here]("http://www.tuxera.com/forum/viewtopic.php?f=3&t=124").

I have ntfs-3g installed and it is currently being used for my 320gb ntfs partitions. No option to format my 1tb to ntfs. Only ext/fat/swap are selectable. :)
My only guess is that I would have to change my partition table to something more windows friendly, but I thought I already selected msdos, which is the best windows friendly one...

fdisk -l
> Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7720    62010868+  83  Linux
/dev/sda2            7721        7783      506047+   5  Extended
/dev/sda5            7721        7783      506016   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x221b01b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1019     8185086   12  Compaq diagnostics
/dev/sdb2   *        1020        7450    51657007+   7  HPFS/NTFS
/dev/sdb3            7451       38913   252726547+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ea19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      118270   949999968+  83  Linux


EDIT:
Apparently using system->admin->disk utility it says I can format my unformatted space to NTFS... Havn't clicked "create" yet to see if it would work.
[[IMG]http://img97.imageshack.us/img97/6214/screenshotpalimpsestdis.png[/IMG]](http://img97.imageshack.us/i/screenshotpalimpsestdis.png/)

---

### Post by SeePU on 2010-02-16
> **andrewabc said:**
> I've always been able to make ntfs partitions on my old hard drive using gparted. Not sure why not able to easily do so on my new hard drive. Must be a setting somewhere when I made the partitions. I thought I made msdos, and though most compatible with windows...XP and Windows 7 both use NTFS but they obviously set up partitions differently.

When gparted creates an NTFS partition, it is probably more similar or compatible to an XP NTFS system than a Windows 7 NTFS system.  Afterall, developers of Parted and Linux partition tools were trying to simulate NTFS from XP/2000, not Windows 7.  Hopefully, they will address compatibility with Windows' 7 NTFS soon as they would also address the partition alignment issue, too.

Because of this, I don't think it is worth your time trying to create an NTFS partition from GParted.  At least, not from the GUI.  I suspect you need the CLI as you need some commands to make some adjustments to the partition alignment.  I usually leave most of the defaults so I don't recall how many options are given.  I know you can change the boundaries but you need more options.  From what I read, it sounds like the default GUI tools for partitioning in Linux has not addressed 4096-byte sector drives yet.

---

### Post by SeePU on 2010-02-16
Btw, my assessment was applicable to 4096-byte sector drives as you could use GParted as before with any drive not using the Advanced Format.  The old style drives can be used as before but I read that drive manufacturers are going to move to the new format.

---

### Post by antiram on 2010-02-16
> **SeePU said:**
>   Hopefully, they will address compatibility with Windows' 7 NTFS soon as they would also address the partition alignment issue, too.
the ntfs disk format is unchanged since ages, also the cluster size of 4k (default on every filesystem). Cluster != sector.

W7 use 1024k alignment. If someone want to do that with fdisk, then set startsector to 2048 or a multiple of 2048.

Another way is "fdisk -S32 -H32 /dev/sda". It sets the sectors and heads of a cylinder to 32. A cylinder has now 1024k size and you can use cylinder alignment.

> **andrewabc said:**
> 
I'm confused what to put in now. just 1953525167 ? Or 995g for a 995gb partition leaving ~5 gb unpartitioned space? I'm not sure how many gb I can put in.
press enter or 1953525167 for one big partition without leaving space. The difference of 5GB? is because
[http://en.wikipedia.org/wiki/Mebibyte](http://en.wikipedia.org/wiki/Mebibyte)

you can also resize the your big ntfs partition with gparted to use the rest of 27GB or GiB.

This could also work with gparted for alignment:
make new partition table and a new partiton. Disable the "align to cylinder boundary" checkbox and let 1MB free space before the partition. If it works fdisk -lu should show startsector at 2048.

can you post the output of "hdparm -I /dev/sdc"? It should show the logical and physical sector size.

---

### Post by cyberey66 on 2010-02-17
> **andrewabc said:**
> I got impatient and formatted to ext4.


Backing up files/folders to drive now. Says I'm getting 47mb/s (now 41) speed.

Can you please post what you used to partition the drive, with what setting, and which file-system is used?

I am going to receive this drive in a few days and it would save me and many others a lot of time if a proven work around is posted.

I assume this is a WD green drive, have you been award to the other issue this drive has with its 'intellipark' feature?  [http://bbs.archlinux.org/viewtopic.php?id=73573](http://bbs.archlinux.org/viewtopic.php?id=73573)

---

### Post by SeePU on 2010-02-17
cyberey, the OP obtained the newest version of the WD Green drives that has the new format, 4096-byte sector drives.  I think he has a WD10EARS 1TB HDD.

You are referring to the older type of Green drive, they operate the same as the older style except for the powersaving feature they call 'Intelli-Park.'   That would be the WD10EADS series (the number refers to the terabytes - 10 = 1TB and so on).  I don't think the 'EARS' series has the same issue with the load cycle counts or parking heads.  At least, I have not read of any reports of that.  The main issue seems to be the setup of partition alignment.

---

### Post by andrewabc on 2010-02-17
> **cyberey66 said:**
> Can you please post what you used to partition the drive, with what setting, and which file-system is used?

I am going to receive this drive in a few days and it would save me and many others a lot of time if a proven work around is posted.

I assume this is a WD green drive, have you been award to the other issue this drive has with its 'intellipark' feature?  [http://bbs.archlinux.org/viewtopic.php?id=73573](http://bbs.archlinux.org/viewtopic.php?id=73573)

What I did I posted in this thread. Page 2 reply #12. Used gparted to create ext4 partition once the blank partition was created (and supposedly aligned properly). Still got 25gb unpartitioned (as I didn't put in entire number in post #12). Which is fine for me as I might partition to ntfs later to share files with windows computers.

I'm just using my 1tb as data drive with no OS installed to it and it is running in external enclosure using esata connection.

I have 1tb EARS model which has 4k sector. EADS doesn't have 4k sector.

I don't know anything about intellipark feature problem (havn't read anything). The thread you link to is from June 2009, and the drive I have didn't come out until December 2009. So who knows if it has similar problems.

[Western Digital Caviar Green WD10EARS 1TB 5400 RPM 64MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive ](http://www.newegg.ca/Product/Product.aspx?Item=N82E16822136490) is what I got.

---

### Post by SeePU on 2010-02-17
973 usable GB seems good.  My experience with 1GB drives usually is 931GB (following a format) so I'm not sure what's going on there.

[http://compreviews.about.com/od/storage/a/ActualHDSizes.htm](http://compreviews.about.com/od/storage/a/ActualHDSizes.htm)

---

### Post by andrewabc on 2010-02-17
> **SeePU said:**
> 973 usable GB seems good.  My experience with 1GB drives usually is 931GB (following a format) so I'm not sure what's going on there.

[http://compreviews.about.com/od/storage/a/ActualHDSizes.htm](http://compreviews.about.com/od/storage/a/ActualHDSizes.htm)

That 973 you got from one screenshot I think is using different gb measurement. If you go to page 2 of this thread my other picture only shows 891.8 gb for that partition.

So I'm guessing same amount as you thought other 1tb had.

EDIT:
actually that other pic shows 973 as well
[http://img713.imageshack.us/img713/1779/screenshot6bedd91107c14kn.png](http://img713.imageshack.us/img713/1779/screenshot6bedd91107c14kn.png)
Dunno what they mean.

---

### Post by andrewabc on 2010-02-18
Oh, new 4k sector does mean more space available.
[WD Gives You Up To 11% More Space With Advanced Format](http://hothardware.com/News/WD-Gives-You-Up-To-11-More-Space-With-Advanced-Format/)

---

### Post by SeePU on 2010-02-18
> **andrewabc said:**
> Oh, new 4k sector does mean more space available.
[WD Gives You Up To 11% More Space With Advanced Format](http://hothardware.com/News/WD-Gives-You-Up-To-11-More-Space-With-Advanced-Format/)
Hey, Andrew, can you let me know how what you think of your drive?

Maybe keep me updated if you don't mind?   You could pm if it's not too much trouble.

I am thinking of getting the 1.5TB version, the WD15EARS.

I don't have Windows 7 either but I might get it at some point.   I might have to use the same procedure or one mentioned.  I was going to format NTFS, though, to share between Win OS and Linux.

---

### Post by antiram on 2010-02-18
@andrewabc

can you post the output of "hdparm -I /dev/sdc"? It should show the logical and physical sector size.

.33 kernel should do the alignment of filesystems automatically with the logical/physical sector size information. eg. my (every..) ssd has 4k physical, but the ssd doesn't report this. hdparm -I show such features.

also current unstable parted (2.1 or so) use this information.
[http://www.gnu.org/software/parted/manual/parted.html#Invoking-Parted](http://www.gnu.org/software/parted/manual/parted.html#Invoking-Parted)

---

### Post by andrewabc on 2010-02-18
I have put
11,115 items, totalling 124.3 GB
on it so far. Currently just a place to put data from my 320gb hard drive.

Moved 20.7gb 20 files from 320gb to 1tb. Took 9 minutes. And while watching tv show from 320gb.
Watched 2 hour 1gb movie from 1tb. Enclosure was a bit warm at the end, but shortly after with no activity it is now cool.
> 
andrew@andrew-desktop:~$ hdparm -I /dev/sdc

/dev/sdc:
 HDIO_DRIVE_CMD(identify) failed: Bad address
andrew@andrew-desktop:~$ hdparm -I /dev/sdc1

/dev/sdc1:
 HDIO_DRIVE_CMD(identify) failed: Bad address

No idea why nothing appearing. I'm using ubuntu 9.10

Just to reiterate, I'm only using this drive to store data. No OS will be installed to it until maybe 10.04 final released. So no idea if I've got it aligned properly (hopefully), or how fast it reacts to OS. Can't easily do benchmarks either because linux sucks at benchmarks and not installing windows to it (winxp doesn't recognize the drive, but I havn't installed drivers yet).
According to benchmarks I've seen it's supposed to get 100mb/s read/write according to atto. And good results on crystaldisk.
I'm on ICH8 with SSD, 320gb, 1tb, and DVD rw all on SATA. So all that connected will slow things down as well.

So if you are upgrading from older hard drive it should be good. My 320gb hard drive only has 8mb cache, so the 64mb I would think make it much faster. Although 5400RPM, I guess that is supposed to use less power/heat/noise. I have SSD so speed not an issue. I just want to store data instead of having to burn to DVD like I've been doing. DVD archival sucks.

---

### Post by SeePU on 2010-02-18
I want the drive for the same thing, storage.  It's too slow for an OS drive.  The only drives I'd buy new for an OS drive would be a SSD.  I'd install the OS on the SSD, non-essential or non-OS programs and applications on the storage drive as well as writing data there (especially video files for me).

I'd use NTFS so both Windows and Linux can access the drive.

---

### Post by SeePU on 2010-02-18
> **andrewabc said:**
> So no idea if I've got it aligned properly (hopefully), or how fast it reacts to OS. Can't easily do benchmarks either because linux sucks at benchmarks and not installing windows to it (winxp doesn't recognize the drive, but Windows won't recognize it because you formatted it ext4.  You'd need those obscure 'drivers' or utilities that can 'access' ext2/ext3 but I'm not sure if it's compatible with ext4.  I've never used those.

---

### Post by cyberey66 on 2010-02-20
The solution:

run 'fdisk -u'  and make sure the starting sector is a multiple of 8 when partitioning.  You can then format the partitions to whatever system you like.

I tried this with my drive and the speed was increased by changing the starting section to a mulitiple of 8.

If you want to use a GUI, use whatever program you would normally use and setup your drive.  Run fdisk -u and then print the partition table.  If the starting sectors are not a multiple of 8, write down the numbers and add sections until they are.  Then use fdisk to great the new partitions with these starting sectors.

WD has a boot cd that supposed to do this by itself.  You can get it here, [http://support.wdc.com/product/downloadsw.asp?sid=122](http://support.wdc.com/product/downloadsw.asp?sid=122).  I haven't tried it.

The issue of the 'intellipark' feature is still prevalent though.  It will park the heads every minute or so, making the the drive reach it's specified life span in less than a year.   I'm testing one of the workarounds now.

---

### Post by SeePU on 2010-02-20
> **cyberey66 said:**
> The solution:

run 'fdisk -u'  and make sure the starting sector is a multiple of 8 when partitioning.  You can then format the partitions to whatever system you like.

I tried this with my drive and the speed was increased by changing the starting section to a mulitiple of 8.

If you want to use a GUI, use whatever program you would normally use and setup your drive.  Run fdisk -u and then print the partition table.  If the starting sectors are not a multiple of 8, write down the numbers and add sections until they are.  Then use fdisk to great the new partitions with these starting sectors.

WD has a boot cd that supposed to do this by itself.  You can get it here, [http://support.wdc.com/product/downloadsw.asp?sid=122](http://support.wdc.com/product/downloadsw.asp?sid=122).  I haven't tried it.
It sounds right.  There is similar discussion on the WDC support forums:
[http://community.wdc.com](http://community.wdc.com)

What I am curious about is whether it matters which sector # the partition starts at.  Is there a difference?  The examples I have read have had people create partitions that start at sectors, 32, 40, 56 and 64.  All multiples of 8 but does it matter which one you choose?  What are the implications of each one?  'Not sure if there is much of a consequence of any of them but I'm almost curious enough to register to ask.

> The issue of the 'intellipark' feature is still prevalent though.  It will park the heads every minute or so, making the the drive reach it's specified life span in less than a year.   I'm testing one of the workarounds now.  How do you know this?  Do you refer to the Advanced Format drives?  I have not read of any having that feature.  I thought it was limited to the WDxxEADS series.   ???

---

### Post by cyberey66 on 2010-02-24
> **SeePU said:**
> It sounds right.  There is similar discussion on the WDC support forums:
[http://community.wdc.com](http://community.wdc.com)

What I am curious about is whether it matters which sector # the partition starts at.  Is there a difference?  The examples I have read have had people create partitions that start at sectors, 32, 40, 56 and 64.  All multiples of 8 but does it matter which one you choose?  What are the implications of each one?  'Not sure if there is much of a consequence of any of them but I'm almost curious enough to register to ask.

  How do you know this?  Do you refer to the Advanced Format drives?  I have not read of any having that feature.  I thought it was limited to the WDxxEADS series.   ???

I'm not sure about the implications of choosing a different sector, but any multiple of 8 should be ok.  If you are using multiple partitions, only the first can start a specific number anyways.

For the 'intellipark' issue, that was my mistake.  I was thinking solely about the WD green series of drives and got off of topic.  It has nothing to do with the new 4k sector issue, it just happens the new WD green drives are both 4k drives and have the 'intellipark' issue.  Looking at my drive's current load cycle rate, it will reach its design limit for load/unload cycles (300,000) in 955 days, or just under 3 years, but others have reported reaching this limit in only a few months.  I am using an external USB dock if that is of any interest.

---

### Post by gradinaruvasile on 2010-02-24
My advice is to not use ntfs on Linux. The ntfs-3g driver will slow your system and hog your CPU in some circumstances (id did happen to me lots of times and i got rid of  all my ntfs partitions).
Maybe format to ext3 and get drivers/utilities for windows xp.

---

### Post by SeePU on 2010-03-09
Does the last sector have to be a multiple of 8?

What if you did something like this?

$ sudo fdisk -u /dev/sdc

The number of cylinders for this disk is set to 121601.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK) 

Command (m for help): n
Command action
e extended
p primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-1953525167, default 63): 64 
Last sector, +sectors or +size{K,M,G} (64-1953525167, default 1953525167): 

What if you entered  1953525160 for the last sector?

It's divisible by 4 and 8?

Btw, what do you think of Windows 7 using starting sector 63 and 240 heads?  This is what I read.  Windows utilizes another 'trick' to get the alignment of 4K byte sectors but I'm not sure exactly what that is yet.  So confusing. :-/

---

### Post by Grenage on 2010-03-09
> **cyberey66 said:**
> I'm not sure about the implications of choosing a different sector, but any multiple of 8 should be ok.  If you are using multiple partitions, only the first can start a specific number anyways.

For the 'intellipark' issue, that was my mistake.  I was thinking solely about the WD green series of drives and got off of topic.  It has nothing to do with the new 4k sector issue, it just happens the new WD green drives are both 4k drives and have the 'intellipark' issue.  Looking at my drive's current load cycle rate, it will reach its design limit for load/unload cycles (300,000) in 955 days, or just under 3 years, but others have reported reaching this limit in only a few months.  I am using an external USB dock if that is of any interest.

Apparently there is a tool called *WDIDLE3* from WD that lets you disable the intellipark crap.

---

### Post by tekstr1der on 2010-03-09
> **SeePU said:**
> Does the last sector have to be a multiple of 8?

No. If you have your leftmost primary partition is aligned properly, the others will follow suit.

> **SeePU said:**
> 
Btw, what do you think of Windows 7 using starting sector 63 and 240 heads?  This is what I read.  Windows utilizes another 'trick' to get the alignment of 4K byte sectors but I'm not sure exactly what that is yet.  So confusing. :-/

Windows Vista/7/2008 all default to 1024k partition offset when creating an initial primary partition either during install or when manually using the diskpart tool. This is great for alignment, especially with RAID or SSD's as it allows for most all stripe size/disk number combinations to be properly aligned. For example, my 4-disk RAID-0 has 128k stripes, thus:

> There are two correlations which when satisfied are a fundamental precondition for optimal disk I/O performance. The results of the following calculations must result in an integer value:

```
Partition_Offset ÷ Stripe_Unit_Size

1048576 bytes ÷ 131072 = 8

Stripe_Unit_Size ÷ File_Allocation_Unit_Size 

131072 bytes ÷ 4096 = 32
```

The default partition offset created by Win7 is more than sufficient to deal with 4k sectors. All this is assuming that you are using RAID or an SSD and alignment is critical. For single-disk setups, alignment is a non-issue.

---

### Post by andrewabc on 2010-03-09
I presume if the very last is not aligned (it technically would be, but just not a full sector), it would only affect the single one, which wouldn't matter.

As long as first is aligned, that is what would matter.

I guess if you had multiple partitions, and if first partition was misaligned (for whatever reason), you could still create second partition and have it aligned properly if you had it start at proper sector divisible by 8.

---

### Post by SeePU on 2010-03-09
> **tekstr1der said:**
> No. If you have your leftmost primary partition is aligned properly, the others will follow suit.

The default partition offset created by Win7 is more than sufficient to deal with 4k sectors. All this is assuming that you are using RAID or an SSD and alignment is critical. For single-disk setups, alignment is a non-issue.Okay, that sounds accurate.  Since you seem to know what you're talking about :-) , what method do you recommend to set up using ext3 or ext4 format and which file system should you choose?

Can you suggest a mock set of instructions?

Do you think the OP's steps are good?

What I want to do is have two of these drives, one for Windows ('would use Windows 7 to format NTFS) and one for Linux, to use for data (videos, Word Processing files, .isos etc.).  Both would be used for data.  Both would be one partition via the entire drive.  

For Linux, just use the steps described in this thread and use expert mode in fdisk?

---

### Post by SeePU on 2010-03-09
> **andrewabc said:**
> I presume if the very last is not aligned (it technically would be, but just not a full sector), it would only affect the single one, which wouldn't matter.

As long as first is aligned, that is what would matter.

I guess if you had multiple partitions, and if first partition was misaligned (for whatever reason), you could still create second partition and have it aligned properly if you had it start at proper sector divisible by 8.I guess that makes sense if it's one partition on the disk, that setting the first sector might calculate it.  But, I have read that you need to offset it.  I'm too confused on the issue right now, though, so I really shouldn't comment. :)

---

### Post by tekstr1der on 2010-03-09
> **SeePU said:**
> Okay, that sounds accurate.  Since you seem to know what you're talking about :-) , what method do you recommend to set up using ext3 or ext4 format and which file system should you choose?
File system choice is completely yours based on merits and advantages.

> **SeePU said:**
> Can you suggest a mock set of instructions?
I could, if I had more time.
> **SeePU said:**
> Do you think the OP's steps are good?
Don't know. Just answering your specific post
> **SeePU said:**
> 
What I want to do is have two of these drives, one for Windows ('would use Windows 7 to format NTFS) and one for Linux, to use for data (videos, Word Processing files, .isos etc.).  Both would be used for data.  Both would be one partition via the entire drive.

For Windows, you don't need to do anything. As long as you let Win7 installer create the primary partition during install, it will be aligned to 1024k.
> **SeePU said:**
> 
For Linux, just use the steps described in this thread and use expert mode in fdisk?
I would not. I have done this exclusively with a gparted live cd and used the parted CLI component in that environment. You can also just use the GUI component and untick "align to cylinders" and leave 1 MiB free space before the partition. Also, be careful with the differences between MB and MiB, KB and KiB, etc. This is the reason I used parted CLI and change my units to bytes;]

Also, I've used this specific technique to align windows/linux installations which existed long before I learned of the advantages of partition alignment. GParted/parted are very powerful.

One last thing. Please tell me you are using an SSD or have a RAID setup? As I said my first post, if this is a single partition on a single disk, none of this matters and we are both wasting time here.

---

### Post by andrewabc on 2010-03-11
Just noticed a PM by seepu, so I'll reply here for a question that wasn't answered yet:

I havn't done any benchmarks on the drive. And it has been turned off for a week or so. At the moment I'm only going to use it to store media once my old hard drive gets full, I move data onto 1tb.

My old hard drive is 8mb cache 320gb 7200RPM
new is 64mb cache 1tb 5400RPM
So I am guessing compared to my old hard drive it is faster. And based upon benchmarks I did on my old hard drive of 70mb/s read/write in atto vs 100mb/s for 1tb random online benchmark.

Crystaldisk benchmark shows 1tb to be much faster. left side is my old hard drive. right side is random online benchmark for same device.

So if you have an old hard drive, then performance wise it should be an improvement. But it shouldn't be an improvement over a newer 7200 RPM drive with say 32mb cache.
They should be fine as long as your not expecting lots of speed, as that is not what the market segment the 'green' drives are targeting. Low power, low heat, low noise, good storage is the market. Since I have SSD for OS and programs it does what it is supposed to do for me.

If speed is an issue then you would want WD caviar black models. Or SSD for OS/programs, and green drive (or your old hard drive) for data/media.

---

### Post by SeePU on 2010-03-11
> **tekstr1der said:**
> File system choice is completely yours based on merits and advantages.

Also, I've used this specific technique to align windows/linux installations which existed long before I learned of the advantages of partition alignment. GParted/parted are very powerful.

One last thing. Please tell me you are using an SSD or have a RAID setup? As I said my first post, if this is a single partition on a single disk, none of this matters and we are both wasting time here.No, not a waste of time and you are wrong here.

The whole point is these drives are factory set wrong.  There's a lot of articles out there about this and links specific to Linux.  I do agree with one thing, it does sound like setting the starting sector to 64 is sufficient for aligning the partition if it is just one large one used.  I think I am ready to try a WDxxEARS drive because this is what I want to do.  I only need it for storage.

These drives are different than the traditional ones so they need any partition to be set up aligned.  WD probably did most of their testing on Vista and 7 so it was good enough for them.  There is a jumper you can set for XP or a utility for alignment in XP.  They probably just made a deal with Paragon and let them set it up.  The point is, GParted, right now DOES NOT set up the alignment properly and you need fdisk or parted to manually do it.  Even if just one partition is used.  However, I read that the developers of the partition tools is working on it so maybe it's fixed now, I'm not sure.

You might still disagree with me but I am not taking any chances since if the partition is not aligned, the drive will be extra slow.  I noticed Fedora 13, System Rescue CD and Parted Magic have updated versions (most of these are beta but nevertheless...) with notes about supporting 4Kb sector disks.  It will be interesting to try but at least I know changing the first sector to a multiple of 8 (like 64) is enough for using one partition.

---

### Post by tekstr1der on 2010-03-11
> **SeePU said:**
> No, not a waste of time and you are wrong here.


Haha.. I neglected to remember the original topic regarding 4096-Byte sectors. I've not seen anything to indicate there would be any reason to align a single partition/single drive. In fact, the entire concept and purpose of partition alignment is based on multiple drives, or in the case of SSD's, internal drive controllers that act as interal RAID. The purpose of this is to reduce unnecessary read/write overhead as a result of misalignment.


[IMG]http://www.ocztechnologyforum.com/forum/attachment.php?attachmentid=10963&d=1247139944[/IMG]

Of course there is no detrimental effects from aligning your partition, so if it indeed enhances the performance of the new 4096 Byte drives, then have at it. It is very easy to do as I described in my previous post using a GParted live-CD and the parted CLI component. Or just create your partition w/ Win7 installation media. There's no reason to try to make the smallest starting offset possible. 1024KiB, or 1MiB, wasted space is hardly a concern these days, I hope :]

---

### Post by MacUntu on 2010-03-11
> **tekstr1der said:**
> I've not seen anything to indicate there would be any reason to align a single partition/single drive.

Maybe I've got something wrong, but those benches on XP look like a reason: [http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2](http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2)

---

### Post by tekstr1der on 2010-03-11
> **MacUntu said:**
> Maybe I've got something wrong, but those benches on XP look like a reason: [http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2](http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2)

Great, if that is accurate, do it to it. Like I said, it will not hurt. I always have raid systems to deal with in my work as a sysadmin and I am a huge proponent of partition alignment. Also, keep in mind that those benches are with XP ( a ten-year old OS ) Using a modern OS like Vista or Win7 (the OS in question that I originally responded to) makes this a moot issue as they create a large enough partition offset by default. Being that this is an Ubuntu forum, yes you will need to create this offset yourself with the tool of your choice. I use parted. It's easy, mature, and accurate.

For more info on how this relates to your Ubuntu install, the following bug:

Lucid Default live-cd install fails with 4K sector / Advanced Format drives
[https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/530071](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/530071)
```

This bug was fixed in the package partman-base - 138ubuntu3

---------------
partman-base (138ubuntu3) lucid; urgency=low

  * Apply optimal alignment constraints to new partitions, or when
    maximising an extended partition (LP: #530071).
  * Add an ALIGNMENT_OFFSET command which can be used to detect whether a
    partition is misaligned.

```
Was just marked fixed!

---

### Post by reedzsu on 2010-04-09
I had tried to install lubuntu 10.04 beta1 in my newly samsung s1 mini protable hard driver.

   [LEFT][LEFT][COLOR=Green]samsung s1[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=0, size=20000000000, type=0x83[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]Entering MS-DOS parser (offset=0, size=120034123776)[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]MSDOS_MAGIC found[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]looking at part 0 (offset 0, size 0, type 0x00)[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]new part entry[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]looking at part 1 (offset 0, size 0, type 0x00)[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]new part entry[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]looking at part 2 (offset 0, size 0, type 0x00)[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]new part entry[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]looking at part 3 (offset 0, size 0, type 0x00)[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]new part entry[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]Exiting MS-DOS parser[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]MSDOS partition table detected[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]containing partition table scheme = 0[/COLOR][/LEFT][/LEFT]
  [LEFT][LEFT][COLOR=Green]Warning: Device /dev/sdc has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.[/COLOR][/LEFT][/LEFT]

---

### Post by discord on 2010-04-22
So is linux prepared for these drives yet? I was going to buy a WD 2.5" 640gb one and put it in a portable USB case, but wanna wait until we can partition these things properly. Somebody please let me know when I won't take a performance and or size hit.

---

