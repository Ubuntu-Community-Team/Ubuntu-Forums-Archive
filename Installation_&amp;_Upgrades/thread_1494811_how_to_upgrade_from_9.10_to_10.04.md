---
title: "how to upgrade from 9.10 to 10.04 ?"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-05-27
hi all,

i would like to upgrade my current installation of U 9.10 to 10.04 LTS.
although i have an installation CD, i discovered recently that i will need what is called an "alternate install" CD.
can someone please tell me where i can get download on the ubuntu page? the downloads section doesn't seem to be working.

is there some other way in which i can upgrade from 9.10 to 10.04 ?

should i instead use manual partition to install 10.04 on the current 9.04 partition ?

should i keep the file system as ext 3 or ext 4 ?

thanks !

---

### Post by WinRiddance on 2010-05-27
> **AM_SOS said:**
> hi all,

i would like to upgrade my current installation of U 9.10 to 10.04 LTS.
although i have an installation CD, i discovered recently that i will need what is called an "alternate install" CD.
can someone please tell me where i can get download on the ubuntu page? the downloads section doesn't seem to be working.

is there some other way in which i can upgrade from 9.10 to 10.04 ?

should i instead use manual partition to install 10.04 on the current 9.04 partition ?

should i keep the file system as ext 3 or ext 4 ?

thanks !

As far as I know the "alternate" CD is also the text based installation CD that can be downloaded directly from ubuntu.com but why the downloads won't work is beyond me. Never seen that happen before.

Also, it is highly recommended that you **make use of the ext4 file system** since that's become the standard since version 9.10 Karmic. From what I'm reading here, what you ought to do is backup your entire home/user folder to a safe location, perhaps a USB stick with admin privileges or another partition on your hard disk. Then I'd go ahead and _reformat that entire partition_ (with your old Ubuntu) from scratch with **ext4** and I'd also create a swap partition around 4 GB in size if your machine is a bit older.

I don't know why you'd have to use an alternate CD for your installation if you didn't have to do that with Ubuntu 9.04 Jaunty or 9.10 Karmic. If you had one of those installed from a regular LiveCD then I don't see any reason what that shouldn't work this time around ...
Good luck.

---

### Post by dE_logics on 2010-05-27
```
sudo apt-get dist-upgrade
``` in terminal.

---

### Post by kansasnoob on 2010-05-27
> should i instead use manual partition to install 10.04 on the current 9.04 partition ?

Do you currently have a dual-boot of 9.04 and 9.10?

---

### Post by WinRiddance on 2010-05-27
If I understood the initial post correctly Ubuntu has not been installed yet. The questions had to do with the proper or best installation method before getting started. The sudo command ... 

sudo apt-get dist-upgrade 
... will to my knowledge NOT upgrade the partition from ext3 to ext4 which is highly recommended. That's why I mentioned just reformatting the existing Ubuntu partition after making a backup of the current user files. Ah well ...

---

### Post by AM_SOS on 2010-05-27
1- i use dual boot and run XP along with ubuntu

2- due to some construction work in this area, i am not confident of the internet update from 9.10 to 10.04. this option is of course the recommended one and upgrades 9.10 directly to 10.04 over the internet.

3- i checked in GPart and unfortunately my FS is still ext 3. so how do i ensure that it is made ext 4 this time ? i think it should be easy with manual partitioning but what happens if i use the automatic installation during the installations ?

4- is it a good idea to format the current 9.10 partition ( which is located within the E: drive of XP ) and install 10.04 over this using the normal installation CD ?

my computer ( toshiba A200) is 2.5 yrs old.

thanks!

---

### Post by kansasnoob on 2010-05-28
Well, what confused me was you saying:

> is there some other way in which i can upgrade from 9.10 to 10.04 ?

**should i instead use manual partition to install 10.04 on the current 9.04 partition ?**

See where you said 9.10 to 10.04 but later mention 9.04?

I'd kind of like to see the output of the Boot Info Script before I make any recommendations:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Regarding ext4:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance%20regressions%20with%20ext4%20under%20certain%20workloads](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance%20regressions%20with%20ext4%20under%20certain%20workloads)

> Performance regressions with ext4 under certain workloads

The default file system for installations of Ubuntu 10.04 LTS is ext4, the latest version in the popular series of Linux extended file systems. ext4 includes a number of performance tuning changes relative to previous versions such as ext3, the file system used by default up to Ubuntu 9.04. These generally produce improvements, but **[COLOR="Red"]some particular workloads are known to be significantly slower when using ext4 than when using ext3[/COLOR]**. If you have performance-sensitive applications, we recommend that you run benchmarks using multiple file systems in your environment and select the most appropriate.

In particular, the dpkg package manager is known to run significantly slower on ext4, causing installations using the server or alternate install CD to take on the order of twice as long as before. ext4 does not guarantee atomic renames of new files over existing files in the event of a power failure shortly after the rename, and so dpkg needs to force the contents of the new file out to disk before renaming it in order to avoid leaving corrupt zero-length files after power failures. This operation involves waiting for the disk significantly more than it strictly needs to, and so degrades performance. **[COLOR="Red"]If fast package management operations are most important to you, then you should use ext3 instead.[/COLOR]** (570805)

The simplest way to select a different file system such as ext3 at installation time is to add the partman/default_filesystem=ext3 boot parameter when starting the installer. If you are deploying Ubuntu automatically using Kickstart or preseeding, then you can set a different file system in the partitioning recipe instead. 

I still use ext3 :)

I'm waiting for btrfs:

[http://digitizor.com/2010/05/15/breaking-news-btrfs-might-be-the-default-file-system-in-ubuntu-10-10/](http://digitizor.com/2010/05/15/breaking-news-btrfs-might-be-the-default-file-system-in-ubuntu-10-10/)

---

### Post by kansasnoob on 2010-05-28
If you choose to upgrade be sure to dodge this bullet:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

It's almost never a good idea to install grub to a pbr rather than an mbr.

---

### Post by AM_SOS on 2010-05-28
hi kansasnoob,
thanks a lot for the installation tip !
frankly, all this is a little difficult for me to grasp, let alone to implement while installation. although i do think that grub is what allows me to select between XP or ubuntu at startup.
so let me go ahead and ask you to please point to a link or message me possible problems that i might have to deal with while installing 10.04 .
btw, i think that rather than upgrading to 10.04 from the update manager, i will instead boot from the 10.04 live CD and use manual partition to make a fresh install over the existing 9.10 install .
thanks !

---

### Post by kansasnoob on 2010-05-28
Partly in response to your PM to me:

> thanks kansasnoob for alerting me of the cons of ext 4.
you are right about the confusion which was inadvertently caused by a typo error on my part. sorry about that..

as you would have gathered by now, i am not an expert when it comes to the innards of the ubuntu OS.
someone else on the pages of this forum told me that it would not be possible to upgrade over the internet using update manager since my current install of 9.10 is ext 3. he suggested a fresh install using the live CD.

btw, do you think it would be a good idea to install 10.04 with ext 3 and not ext 4 ? basically, i use the ubuntu installation for basic stuff such as watching movies, listening to music, surfing the net, and opening and exchanging data from the XP drives.

although i have had no serious problems with ubuntu (since i started out with 8.10) this time i am feeling a little anxious while preparing to upgrade.

thanks !

First of all, if 9.10 is running OK please be patient :)

If it's not running well I would not even consider an upgrade to 10.04. Upgrades seem to work well if the OS being upgraded is working well to begin with, not so much if the OS being upgraded already has problems.

Whether you use ext3 or ext4 is up to you. I prefer ext3 and I've tried both. I believe btrfs should be great! Maybe we'll see it in 10.10, maybe not :confused:

So, what's the burning need to upgrade from Karmic to Lucid?

---

### Post by kansasnoob on 2010-05-28
If you want me to make more suggestions about upgrading run this command:

```
sudo fdisk -l
```

BTW that's a lower case L. Then look at the output, example:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       11693    52002405   83  Linux
/dev/sda4           31366       60801   236444639+   5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux

Partition table entries are not in disk order

Disk **[COLOR="Red"]/dev/sdb[/COLOR]**: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cc7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2646    21253963+   7  HPFS/NTFS
/dev/sdb2            2647        3680     8305605   83  Linux
/dev/sdb3            3681        4708     8257410   83  Linux
/dev/sdb4            4709        9729    40331182+   5  Extended
/dev/sdb5            9449        9729     2257132+  82  Linux swap / Solaris
/dev/sdb6            4709        7078    19036962   83  Linux
/dev/sdb7            7079        9448    19036993+  83  Linux

Partition table entries are not in disk order

```

You can see that I've highlighted the drive designations in red and you'll notice that fdisk ends with, "Partition table entries are not in disk order" so depending on what that shows run:

```
sudo parted /dev/sd**[COLOR="Red"]X[/COLOR]** print
```

Of course **[COLOR="Red"]X[/COLOR]** must be replaced by the proper drive designation.

Example:

```
lance@lance-desktop:~$ sudo parted /dev/sda print
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3            boot
 2      21.5GB  42.9GB  21.5GB  primary   ext3
 3      42.9GB  96.2GB  53.3GB  primary   ext3
 4      258GB   500GB   242GB   extended
12      258GB   280GB   21.6GB  logical   ext2
11      280GB   301GB   21.7GB  logical   ext2
10      301GB   323GB   21.8GB  logical   ext3
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)

lance@lance-desktop:~$ sudo parted /dev/sdb print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.8GB  21.8GB  primary   ntfs
 2      21.8GB  30.3GB  8505MB  primary   ext3
 3      30.3GB  38.7GB  8456MB  primary   ext3
 4      38.7GB  80.0GB  41.3GB  extended
 6      38.7GB  58.2GB  19.5GB  logical   ext3
 7      58.2GB  77.7GB  19.5GB  logical   ext3
 5      77.7GB  80.0GB  2311MB  logical   linux-swap(v1)

```

---

### Post by AM_SOS on 2010-05-31
hi !
well actually 9.10 is running pretty smooth and i quite like the visual look.
also tried out the 10.04 live CD and not sure where all those much talked about visual improvements are :(

so why do i want to upgrade ? see i want to keep in touch with the updates and it seems that updates for the non LTS versions are discontinued after 1 yr of release..
another thing i had noticed with ubuntu / xp is that the OS tends to run smooth if they are kept fully updated.

BUT i am becoming quite interested in the LTS releases. for the simply reason that i won't be able to find the time to keep updating the OS every 6 months and the risks that are attendant in this process. so seriously thinking of sticking to the LTS release !

basically, i do movies, music, internet, and of course virus cleaning / prevention usuing ubuntu.
so am still not sure if e.g. all those codecs (or whatever) will keep updating in the internet, movie players etc. if i stick to LTS..

thanks again !

PS- will run the tests you asked for in a day or two, if that's ok with you. i appreciate the time you are taking out !

---

### Post by AM_SOS on 2010-05-31
hi !

below are the results of the tests that you wanted me to run. as you can see i never got the message - "partitions table entries are not in disk order".
however, i went ahead and the results are displayed below in the order you mentioned in your last mail.

for the first i used " sudo fdisk -l ". the result is -

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1d0a7d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       14593    91618695    f  W95 Ext'd (LBA)
/dev/sda5            3188        7011    30716248+   7  HPFS/NTFS
/dev/sda6            7012       11854    38901366    7  HPFS/NTFS
/dev/sda7           11855       14286    19535008+  83  Linux
/dev/sda8           14287       14593     2465946   82  Linux swap / Solaris


``` 

for the second, i used " sudo parted /dev/sda print ". the result is -

```
Model: ATA TOSHIBA MK1237GS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  26.2GB  26.2GB  primary   ntfs            boot
 2      26.2GB  120GB   93.8GB  extended                  lba
 5      26.2GB  57.7GB  31.5GB  logical   ntfs
 6      57.7GB  97.5GB  39.8GB  logical   ntfs
 7      97.5GB  118GB   20.0GB  logical   ext3
 8      118GB   120GB   2525MB  logical   linux-swap(v1)
```

so hope this provides you the information you wanted first,
awaiting your respons,
thanks !

---

### Post by kansasnoob on 2010-05-31
It may be tomorrow before I have time to really look at this. I'm dealing with sick animals right now and I'd have trouble spelling my own name.

---

