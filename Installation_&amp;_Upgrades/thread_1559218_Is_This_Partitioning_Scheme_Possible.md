---
title: "Is This Partitioning Scheme Possible?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-08-23
[SIZE="6"]Is the following partitioning scenario possible?[/SIZE]

**Partition 1 NTFS:** (primary) *Windows 7 Ultimate 64 bit*

**Recovery Partition NTFS 2:** (primary)This is the *Recover Disk* made by windows (does it really count as a one of the four primary partitions?

**Partition ext4 3:** (primary)*Ubuntu 10.04 64 bit* with a shortcut to /home (symlinked to the mounted home in Logical partition 2, which is mentioned further down)

**Partition 4:** (extended)*Data Exchange*. I want both operating systems to use the same data for documents, music, videos, images etc. 
   **-Logical 1 FAT32:** This will house all the data such as music, videos,images and documents (no config or temp files) from both Windows 7 and Ubuntu. these media and document files will be symlinked to Logical partition 2.

   **-Logical 2 ext4:** I will mount the home directory here and have its media and docs symlinked to logical partition 1. Thus it will have the media and docs from windows 7 and the config and setting files required for ubuntu, making it a real home directory.


Can I later use the extended partition for installing an OS such as google chrome os and OSX???

---

### Post by dgoosens on 2010-08-23
> **daksai3 said:**
> 
**Partition 4:** (extended)*Data Exchange*. I want both operating systems to use the same data for documents, music, videos, images etc. 
   **-Logical 1 FAT32:** This will house all the data such as music, videos,images and documents (no config or temp files) from both Windows 7 and Ubuntu. these media and document files will be symlinked to Logical partition 2.



I'd avoid FAT-32...
You will not be able to store big files that are bigger than 4Gb...
FAT-32 is deprecated...

Just make a NTFS of it...
Ubuntu is smart enough to work with that (even shared my mails using Thunderbird in these two OSes

Obviously, the real question is...
Do you really need a Windows partition ?
Depending on what you need it for, would a Virtual Machine (V-box) not suffice ?

dGo

---

### Post by daksai3 on 2010-08-23
> Just make a NTFS of it...
Ubuntu is smart enough to work with that 

Wow, You might be right, but im not sure what you meant. Are you saying that both logical drives should be NTFS and that even though the Ubuntu partition is ext4 the symlink will work?

will ubuntu automatically "convert" between these two file systems.


> Obviously, the real question is...
Do you really need a Windows partition ?
Depending on what you need it for, would a Virtual Machine (V-box) not suffice ? 


virtual box's are not as good as the real stuff, and im not ready yet. im just doing this to see if it is actually as good as it sounds.

---

### Post by dgoosens on 2010-08-24
> **daksai3 said:**
> Wow, You might be right, but im not sure what you meant. Are you saying that both logical drives should be NTFS and that even though the Ubuntu partition is ext4 the symlink will work?

will ubuntu automatically "convert" between these two file systems.


NTFS only for the Exchange partition you wish to create... right...
Ubuntu won't run on NTFS
That would be ridiculous as ext3 and ext4 are far better...

Once the Exchange partition is created, you can automount it on logon...

---

### Post by daksai3 on 2010-08-24
[SIZE="4"]Is this New Partitioning Scenario possible pls rate[/SIZE]

**Partition 1 NTFS 40gb:** (primary) *Windows 7 Ultimate 64 bit*

**Recovery Partition 2 NTFS 10gb:** (primary)This is the *Recovery Disk* made by Windows, but does it really count as a one of the four primary partitions?

**Partition 3 ext4 40gb:** (primary)*Ubuntu 10.04 64 bit* With the /home found here simply containing two symlinks. The **first** being a symlink to the mounted Data Exchange/ Storage in Logical Partition 1 NTSF which will contain all personal documents and media files. The **second** being a symlink to the mounted /home in Logical Partition 2 ext4 which will contain ONLY the configuration files, settings and the hidden files.  The symlinks will only be there for easier manual access to both partitions.  

**Partition 4:** (extended)*Data Exchange*. I want both operating systems to use the same data for documents, music, videos, images etc. 
   
   **-Logical 1 NTSF 15gb:** This will house all the data such as music, videos, images and documents (no config or temp files) from both Windows 7 and Ubuntu. The Personal folders in the symlinked /home drive in the Ubuntu Partition will be symlinked to these.

   **-Logical 2 ext4 15gb:** I will mount the config and setting files from the /home drive required for ubuntu. This will be mounted as the /home directory with a line in fstab. 
   **-Logical 3 SWAP 3gb:** I only have 3 gbs of RAM so I'm assuming that I should use 2-3gbs of  SWAP space.   

Can I later use the extended partition for installing an OS such as google chrome os and OSX???

This will all use about 123 gb of space. I have 640 gigabytes with 517 gigabytes left after this installation. If there is any method for the partition sizes to be flexible and adjust according to what it needs at anytime it'd be great knowing how. 


Why I'm doing this:
This is probably the best solution that separates everything from interfering with each other. The only problem I will have after this partitioning will be to restore the symlinks and remounting the /home directory in Logical Partition 2. 


I can do system reinstalls and many times as I want, without the risk of corruption. 

So if you see any problems or faults in this scheme please point them out. 

Ugh...I wrote too much. :popcorn::popcorn:


thanks dgoosens

---

### Post by daksai3 on 2010-08-24
helpito meep 

bumpito

---

### Post by bachinchi on 2010-08-24
I would put all Ubuntu stuff in the logical partition, just in case you later need a primary partition.
Also, as Win7 is heavy, 40GB may not be the enough (except if you install the programs in another partition). The 3GB swap is a bit excessive for the amount of RAM you have, 2GB should be fine.
The Recovery Partition** _does count_** as a primary partition (I hate that part of the recovery system of HP).

As you have plenty of space I would recommend something like this:

*** Partition 1 NTFS 70GB: **Win7[B]
* Partition 2 NTFS 10 GB: [/B]Recovery
[B]* Extended Partition:
** Logical 1 SWAP 2GB
** Logical 2 NTFS 120GB: [/B]Multimedia takes a *lot* of space.
**** Logical 3 EXT4 40GB**: / (root) partition for Ubuntu.
**** Logical 4 EXT4 3GB**: /home (linking to the actual data)

You can later add any other partition if you wish. My current partition scheme is pretty much like a pointed above.

---

### Post by brr872002 on 2010-08-24
> **daksai3 said:**
> helpito meep 

bumpito
  you can use your partions as you like just edit your /etc/fstab:popcorn:
this may help you !
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=a890bb2d-585b-439a-afb2-e9bf1b0ca9c1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=7cebbab1-a7ec-4776-9c57-2937351e2fef none            swap    sw              0       0
# /dev/sdb6
UUID=43d8d071-62b7-4401-8d38-f1cebd3ba767 none            swap    sw              0       0
# /dev/sdc3
UUID=8cf7de71-023c-4045-9893-781272ad89bb none            swap    sw              0       0
#/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda4               /root/sda4              ext3    defaults        0 0
/dev/sdb5                /home/brr/sdb5            ext3  defaults       0 0
/dev/sda3             /mnt/sda3           ntfs-3g  rw,noexec,nosuid,nodev,noauto,user   0 0
/dev/sdb1             /mnt/sdb1          ntfs-3g  rw,noexec,nosuid,nodev,noauto,user   0 0
/dev/sda1                /mnt/sda1           vfat       defaults        0 0
/dev/sdc1                /mnt/sdc1           vfat       defaults        0 0
/dev/sda4                 /home/brr/sda4         ext3    defaults        0 0
/dev/sdb3             /mnt/sdb3           vfat        defaults        0 0
#/dev/sdc4                /root/sdc4            ext3  defaults       0 0
#/dev/sdc5               /root/sdc5           ext3  defaults       0 0
/dev/sdb4                 /home/brr/sdb4         ext3    defaults        0 0
/dev/sdc4             /mnt/sdc4           ntfs-3g  rw,noexec,nosuid,nodev,noauto,user   0 0

---

### Post by tommcd on 2010-08-24
> **bachinchi said:**
> 
As you have plenty of space I would recommend something like this:
**** Logical 3 EXT4 40GB**: / (root) partition for Ubuntu.

Your partitioning scheme looks good, except that 40GB is way too much for root. A full Ubuntu install takes about 3.5GB, if that. I would limit the root partition to 20GB. My laptop has a root partition of 10GB. My desktop has a root partition of 14GB. This has provided me with more than enough space for installing all the apps I want for several years.
My laptop currently has 3.1GB used on it's root partition. My desktop has 3.5GB used on it's root partition.

---

### Post by oldfred on 2010-08-24
I typically recommend 10-20GB for root especially if you have all your data in other partitions. I have several root partitions all 20-25GB (all Ubuntu 9.10, 10.04 & 10.10) plus space for several more system partitions if I want to experiment with others. But I have installed lots of programs and only have used about 6GB and with all my data mounted in /shared or /data. My /home is about 1GB used. (I now have moved /home back into root as it is easy to backup separately).

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

I directly mount my NTFS shared partition into /home but all my standard folders in /home are really in /data and linked in. Since it is just data you can link from the NTFS as well. But I use windows so little now most of my new data is in /data.
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by daksai3 on 2010-08-25
> I would put all Ubuntu stuff in the logical partition, just in case you later need a primary partition.

I want to place all Operating Systems in Primary Partitions just for organizing's sake. I don't plan on installing any other Operating Systems. I also want all data to be in the same place so that I can dedicate only specific amounts of space for each Operating System and thus not risk wasting space and instead give all excess space into recovery and my data files.  

Basically I'm investing more on recovery and data space.

> Also, as Win7 is heavy, 40GB may not be the enough (except if you install the programs in another partition). 

Thanks for that suggestion, I experimented myself and I will do further research on how to safely install my files and their settings in another partition.
 
> The 3GB swap is a bit excessive for the amount of RAM you have, 2GB should be fine.

Alright, I will use 2GB but is the SWAP only for linux? Can I also use it for Windows 7?

> The Recovery Partition does count as a primary partition (I hate that part of the recovery system of HP).
Yea, I have HP. Is it possible to mount the recovery partition (primary) to a logical partition?

> As you have plenty of space I would recommend something like this:

* Partition 1 NTFS 70GB: Win7
* Partition 2 NTFS 10 GB: Recovery
* Extended Partition:
** Logical 1 SWAP 2GB
** Logical 2 NTFS 120GB: Multimedia takes a *lot* of space.
** Logical 3 EXT4 40GB: / (root) partition for Ubuntu.
** Logical 4 EXT4 3GB: /home (linking to the actual data)

so based on what all of you said and what i found elsewhere im gonna do the following:
* Partition 1 NTFS 40GB: Win7 (will place program files and their settings in a logical partition if possible, if i can't it will be 70gb)
* Partition 2 NTFS 10 GB: Recovery (will try to place in a logical partition)
* Extended Partition:
** Logical 1 SWAP 2GB (Unless I decide to later use VMs for experimenting from either OS i might choose to increase.)
** Logical 2 NTFS 120GB: Multimedia takes a *lot* of space. (I will use everything remaining after investing in recovery disks, but I expect it to be at least 120gb)
** Logical 3 EXT4 20GB: / (root) partition for Ubuntu. (I agree that it should be less, but I can surly expand as neccesary, the good thing is that i can simply install these programs when  upgrading to new versions of ubuntu by simply using a list of installed programs and the terminal. The bad thing is that i cant export it like files like i can do with windows's program files.)
** Logical 4 EXT4 5GB: /home (this being the actual data that other will symlink to) 

^^^^thank you bachinchi and olfred for ur excellent input as it is really helping me draw this scheme. ^^^^
> this may help you !
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdc2



this certainly helps, im also looking at a few guides. do u know any really good ones.

---

### Post by daksai3 on 2010-08-25
bump? i need more input pls. i want to hear everyone.

---

### Post by daksai3 on 2010-08-25
harro people?

---

### Post by tommcd on 2010-08-25
> **daksai3 said:**
> 
Alright, I will use 2GB but is the SWAP only for linux? Can I also use it for Windows 7?
No, Windows will not recognize a linux swap partition.
> **daksai3 said:**
> 
Yea, I have HP. Is it possible to mount the recovery partition (primary) to a logical partition?
I don't think so. I would leave the Windows 7 system partition and the recovery partition as primary partitions. Leave the Windows 7 system partition big enough for all the programs you may want.
Windows 7 and Ubuntu can share the NTFS multimedia partition.
The Ubuntu partitions can all be logical.
The 5GB for /home is small, but if you are storing all the multimedia stuff on the NTFS partition, and only use /home for text files and stuff, it should be ok.

---

### Post by daksai3 on 2010-08-27
ok thanks everyone for alll ur great help. im marking this thread as solved. im done with with all my linux questions. sank you!!!

---

