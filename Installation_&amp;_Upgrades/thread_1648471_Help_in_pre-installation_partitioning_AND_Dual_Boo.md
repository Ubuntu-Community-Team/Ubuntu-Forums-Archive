---
title: "Help in pre-installation partitioning AND Dual Boot Vs Virtual OS"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by Amit_Olkar on 2010-12-18
I am now tired of WUBI installs, esp. due to recent GRUB problems. 
I have two questions:
[INDENT][LIST=1]
[*]Should I go for a Dual Boot (non-WUBI) setup or should I install Ubuntu as a Virtual OS within Windows ?

[*]My first choice being Dual Boot system, How to go about partitioning my Drive ?
I have the following setup:
[INDENT][LIST=2]
[*] 2GB RAM
[*] Three primary partitions
[*] "Toshiba System Volume" : 1.46 GB, Free - 1.33 GB, NTFS - Created while installing Windows
[*] "C:" : 80.0 GB, Free - 20.1 GB, NTFS - Windows 7
[*] "D:" : 151.42 GB, Free - 94.21 GB, NTFS - This is where I wish to create my Ubuntu installation
[/LIST][/INDENT]
[/LIST][/INDENT]

I wish to use 50GB from the 94.21GB free space on "D:". I plan to use Ubuntu Ultimate Edition based on Ubuntu 10.04 [http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/]("http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/"). I would like to be able to separate my personal data like home folder so that even if the OS crashes I'll be able to access it through a Live CD or a rescue CD OR even through another possible Linux installation.

So What should be the setup ?
[INDENT][LIST=1]
[*]What should be the partitioning scheme ?
[*]Which partitions to create first i.e. Swap, /, /usr etc.?
[*]Which partitions should be mounted seperately, viz. /, /usr, /var, /tmp etc ?
[/LIST][/INDENT]

The reason for starting this thread is that I have had problems while trying to repartition the hard drive as only 4 primary partitions are permitted, and I was not able to create all the different partitions.

---

### Post by oldfred on 2010-12-18
Use your windows tools to shrink the NTFS partition. Since it is a data partition it should not matter, but it is a little safer. Reboot windows it will probably want to run chkdsk. I do not know if it does that for data partitions or not. If not you should run one chkdsk anyway.

Then create the final sda4 extended partition using gparted for all the free space and create the logical partitions for Ubuntu.
You already have a separate NTFS partition for any data you might want to share with Windows. I have Firefox and Thunderbird profiles in my shared partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

You then use manual install to choose which partition to use as / and its format, which for /home and its format (if reinstalling do not format), and it finds swap if created in advance.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Amit_Olkar on 2010-12-18
> Use your windows tools to shrink the NTFS partition. Since it is a data partition it should not matter, but it is a little safer. Reboot windows it will probably want to run chkdsk. I do not know if it does that for data partitions or not. If not you should run one chkdsk anyway.

Then create the final sda4 extended partition using gparted for all the free space and create the logical partitions for Ubuntu.
You already have a separate NTFS partition for any data you might want to share with Windows. I have Firefox and Thunderbird profiles in my shared partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

You then use manual install to choose which partition to use as / and its format, which for /home and its format (if reinstalling do not format), and it finds swap if created in advance.

So say I shrink my "D:" partition, which is Primary at the moment by 60GB, Should all this 60GB be converted to EXT4 file system ? In that case, will I still be able to create individual partitions inside that 60GB ? 

Or, should I create a 20GB Primary partition & a 40GB Extended Partition, and create the "/" partition on the 20GB primary; a 10GB SWAP (Logical) on Extended Partion,( I prefer to have at least 2 x RAM for SWAP size, but I'm allocating more considering that Ultimate Edition can be heavy on resources ); and rest 30GB as / home (Logical) on the Extended Partition ?

Instead of using built-in  tools for Windows 7, I am using EASEUS Partition Master, which is easier to use, and permits operation queues. 

I don't know if Ubuntu 10.04 use GParted for partitioning, but I have a copy of System Rescue CD from [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") as well as PartedMagic 5.7 from [http://partedmagic.com/]("http://partedmagic.com/"), both of which contain GParted, so that shouldn't be a problem.

---

### Post by oldfred on 2010-12-19
If you have 3 primary the 4th has to be the extended primary partition. The extended is not formated, it is just a container for all the logical partitions. Linux works just fine with all of its partitions in logical partitions. Windows has to boot from a primary.

Be sure not to shrink NTFS partitions too much they need room or they slow down system. 30% is not too much free  space in NTFS. When it gets to 10% free it just about stops working.

---

### Post by Rebelli0us on 2010-12-19
Wny not install Ubu on a USB flash drive? That way there won't be any changes to you windows partitions.

---

### Post by Amit_Olkar on 2010-12-19
@Oldfred, Thanks for your help,  It Works !

Here's the solution that I applied,

[INDENT]
[LIST=1]
[*]Shrinked the 150GB Data Partition, to 90GB, thereby freeing 60GB for Linux
[*]Created a 'New Simple Partition' ( Logical / Extended ) using Windows built-in tool, and kept it as a 'Raw' partition i.e. no filesystem; restarted the system. It scanned the disk and booted into Windows w/o errors.
[*]The booted using GParted Live CD, and created an EXT4 partition for '/' (20GB), and another similar one for '/home' (30GB) and the rest as SWAP area (10 GB).
[*]Restarted and booted into Windows and manually scanned the disk to check everthing was fine.
[*]Restarted and booted using the Ultimate Ubuntu 2.7 DVD, and continued with the standard installation.
[/LIST]
[/INDENT]

---

### Post by oldfred on 2010-12-19
Glad it worked. :)

---

