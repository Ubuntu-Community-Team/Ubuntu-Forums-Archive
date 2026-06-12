---
title: "Confusion about partition size for ubuntu 10.10"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by abu46 on 2011-03-13
hi friends:)

i am a first time user of linux/ubuntu and have some doubts about installing it with windows 7 ultimate pre-installed

here is my scenario:popcorn:

i have a 2x250gb hdds, with 100gb(windows) & 132gb(downloads) + a whole 232gb for data(dont wana use this hdd as its very old)

now if i format the 132gb partition and install ubuntu on this then i guess i wont be able to use it for dumping downloaded files from windows ito this space as windows wont recognize ext file system of linux, right?

what is the least amount of disk space for ubuntu to work properly (while trying installation through wubi, it allocated 17gb by default),coz i was thinking of allocating the least possible space in which ubuntu could work fine from the 132gb partition, would it be ok?? 

provided above is right should a shrink the partiton of 132 from within windows

also what is the ideal swap size for 4gb of ram.

---

### Post by Frogs Hair on 2011-03-13
You have plenty of space , so no problem there , I actually use 30 to 40 gb for Ubuntu because I get the new release every 6 months and most of my music is on cd.  I would increase that if I find a release that I want to use for its life time. Here is some information on partitions .

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by vanadium on 2011-03-13
In a dual boot scenario, I would use about 10 GB for Ubuntu + a partition for swap space (space depends on you RAM). All your user data can be shared with the Windows system, Thus, you only need disk space for the system and for user configuration files, but not for user data on yous Ubuntu system partition.

---

### Post by oldfred on 2011-03-13
You need 4GiB for swap if you want to hibernate. Otherwise 2GB will be fine as with 4GB of RAM you may never use swap unless editing videos or running may large programs at once.

pyschocats has lots of good info, but she has not updated the partition page on shared windows partition. Do not use FAT except for small partitions or external devices that have to have it for compatibility. FAT is not as reliable and has a 4GB max file size that ate a bunch of my data before I converted to NTFS.

My suggestions:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by Animal X on 2011-03-13
> **abu46 said:**
> hi friends:)

what is the least amount of disk space for ubuntu to work properly (while trying installation through wubi, it allocated 17gb by default),coz i was thinking of allocating the least possible space in which ubuntu could work fine from the 132gb partition, would it be ok?? 


also what is the ideal swap size for 4gb of ram.


i have installed ubuntu10.10 into a nominal 8G usb stick, and it worked just as fine as my desktop installation.

swap size is usually figured automatically if ubuntu installs itself, but an old rule of thumb was to match whatever your ram was, but nowadays that can be excessive. i think the reason for matching was to accommodate the pagefile(or linux equivalent?) in the event of a sudden sleep? 1G could be a safe minimum for you?

---

### Post by TenPlus1 on 2011-03-13
I have a desktop with a 10gb partition running Ubuntu and NO swap file because I have 2gb memory, more than enough for my day to day activities and then some...

---

### Post by kagerato on 2011-03-13
I wouldn't recommend using any less than 16 GiB for your root filesystem, but it's absolutely possible to have a functional system with much less than that.  There is no theoretical minimum, but even a thin, streamlined desktop typically needs about a GiB of storage for essential programs and their data files.

This is all assuming you intend to put /home (personal user data) on a separate partition.  If not, you need to consider how much additional data you will be personally storing in /home .

Also, it's true that Windows itself doesn't recognize (for reading or writing) any of the ext filesystems.  However, there is third-party software and tools you can use to accomplish this.

In the reverse case, Linux has had nearly complete NTFS support for quite some time now.  You can usually count on it out-of-the-box, regardless of distribution.

---

### Post by abu46 on 2011-03-14
@all
thnx for all your replies and suggestions


i decided to go with 12gb partition for ubuntu but when i try to install ubuntu i get this type of disk allocation!!

it dosent show any ntfs partitions and takes my 2x250gb hdds as 1 500gb disk
i am not using any type of raid array nor any nvidia sw

also i dont get an option of "install it side by side"

how should i go about it

---

### Post by oldfred on 2011-03-14
/mapper/nvidia is either RAID or LVM, probably RAID. 

What does this show from liveCD?

```
sudo fdisk -lu
```

---

### Post by abu46 on 2011-03-14
i did use an raid0 array on these pair of hdds long time back but since then i fully formated my primary hdd and also i have changed all my hw except hdds

its really strange that ubuntu is still seeing them in raid

is there any workaround for this except formatting the entire hdds?

the partitions are detected from within ubuntu

---

### Post by oldfred on 2011-03-14
Hard drives maintain RAID metadata. If you are sure you are not using RAID ( as this will permanently break the RAID).

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by abu46 on 2011-03-15
**@ oldfred**

thnx man, solved the problem :)

[B]just 1 more question before i finally install ubuntu (decided for a 12gb partiton with 10gb root, no swap & 2gb home, it will be OK right?)

where should i put the boot loader/grub, on the windows partition or the root partition of ubuntu??
have read elsewhere that win7 tends to corrupt grub2
i will be dual booting with windows7 and wana use win7 as my default os for now

also is there a way to use win7's boot loader instead of selecting os from grub
i dont have much knowledge about boot loaders and all :([/B]

---

### Post by oldfred on 2011-03-15
Never, never install grub's boot loader to the windows partition. That has to have windows code in it or windows will not work.

I like grub2 and it boots win7. Grub did a fix for flexnet (DRM manager) which was one of the main problems with win7 software. The others were some Dell & HP utilities that most users just uninstalled as they are not essential.

If you want to be primarily windows there is another third party boot loader that looks like windows and lets you boot Ubuntu.

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by dhandarpooja on 2011-03-15
hi friends i have installed UEC clc,cc,wc on ne machine and nc on other machine .now i have created images and instances.now i have query that how to access VMs created?

---

### Post by abu46 on 2011-03-15
@oldfred

ubuntu is taking my primary hdd /dev/sda(on which windows is installed) as default location for installing boot loader
is it ok to go with it

is this partition scheme ok??
12gb partiton with 10gb root, no swap & 2gb home, it will be OK right?

---

### Post by oldfred on 2011-03-15
@dhandarpooja welcome to the forums, but please start your own thread and try to avoid abbreviations.

@abu46
sda is the drive and that is where you want to install your grub boot loader. You do not want to install to a partition like sda1 or sda2. 

All MBR(msdos) computers boot from BIOS to MBR which then jumps to additional code to continue to boot.

Old IDE systems BIOS would only load from primary master (jumper pins on drive). New SATA drives have an updated BIOS that lets you select which drive is bootable. In effect software switchable masters.

(for those who notice, I did complain to dhandarpooja about  abbreviations and then used a bunch of them. :))

---

### Post by abu46 on 2011-03-15
thnx for clearing that out

final thing:
PLZ COMMENT ON MY PARTITIONING SCHEME

**12gb partiton with 10gb root, no swap (guess 4gb ram is enough) & 2gb home**

---

### Post by oldfred on 2011-03-15
If you are only giving 2GB to /home I would not make it separate. The /home has your user settings which do not take much space and all your data which depends on you. Some do get by without swap but others have suggested to have some swap or a swap file. I have moderately large drives so I just create a 2GB swap partition on every drive, and never hibernate and only let my portable sleep after all running programs are shutdown.

I think my /home has about 1GB used, but I keep all data in separate /data and /shared(NTFS) partitions. Part of the reason I am even using the 1GB is I still have wine with Picasa in it, still in /home. I do not keep /home separate anymore since it is small and easily backed up. Then I backup my data separately.

---

### Post by Hakunka-Matata on 2011-03-15
@oldfred:  Excuse the interruption, I don't know if this is proper etiquette, method to ask you to drop in on [this]("http://ubuntuforums.org/showthread.php?p=10562725#post10562725") thread, if you don't mind.  Tell me the kind way to do it, if you don't mind.  thanks HK

---

### Post by abu46 on 2011-03-16
@oldfred

thnx man you have been really really helpful

i am really getting confused now :(
some installation guides suggest making 4 partitions
-boot -swap -root -home some only two

1. is  it necessary to have a boot partition if yes how much, as far as i understand it the same as win7 reserves 100mb of space
2. root is the same as a C drive, that means all the sw that i install will go to root, right?
3. if i allocate 2gb to swap, will it be ok for sleep
4. i am considering to have /home as i can have a backup of my setting when i reinstall/upgrade

plz suggest best partitioning scheme for my 12gb space, so that i can go ahead and install ubuntu
how about 6gb root+2gb swap+4gb home

---

### Post by Hakunka-Matata on 2011-03-16
[LIST]
[*]1. No, /boot partition is not necessarry.
[*]2. root has the mount point of / (root) all files and folders are within root.  Software goes to a number of different folders within / (root)
[*]	/home folder contains user(s) folder(s) and data
[*]3. Swap space required for sleep/hibernate is equal to installed RAM - 4GB RAM?, then 4GB swap
[*]4. Good approach
[/LIST]

"why so serious?"  notice my username (albeit misspelled!)

---

### Post by abu46 on 2011-03-16
is it absolutely necessary to have ram=swap, will having 2gb swap create problems with sleep??

i dont intend to dump all my files to /home as i intend to use other ntfs partitions for that and only want to have /home as backup for setting etc.
so i guess 4gb is more than sufficient.

all partitions should be logical, right?

---

### Post by Hakunka-Matata on 2011-03-16
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by abu46 on 2011-03-16
thnx for the link

all partitions that i create for linux should be logical, right?

---

### Post by Hakunka-Matata on 2011-03-16
Not necessarily, Linux partitions can be logical or primary.

Windows requires primary partition

Thumbnail as example of Linux partitions

---

### Post by oldfred on 2011-03-16
Having only 12GB total space is not generous. But will work. i do have an install in my 16GB flash using 8GB for everything, no swap & 8GB for data. Some have managed to fit a full install in 4GB, but that is very tight as the default is over 3GB and updates usually take you close to 4GB. You often then should uninstall OO & Firefox and go with smaller applications or use a lighter weight version in the first place.

But with small partitions you have to maintain more, lots of housekeeping, and it is better to have everything in one partition. With separate partitions, you may allocate space to one that you then find you really want for the other. 

Lighter weight Versions use with Chromium browser as it is lighter than firefox:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector
Install to old Toshiba - Lubuntu
[http://ubuntuforums.org/showthread.php?t=1634538](http://ubuntuforums.org/showthread.php?t=1634538)

Herman on advantages/disadvantages of separate system partitions post#3 - He also likes swap files not swap partitions.
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by jre6 on 2011-03-16
Well, since you are new to Ubuntu, I will recommend it the easier way :

Firstly, make a backup if necessary.

When you install Ubuntu 10.10, you should usually get a graph, showing Ubuntu 10.10 and other OSes side by side, and then you can drag it to control your partitions. If you went to the advanced mode, try the normal mode which I described. If it fails and directly goes into the advanced mode, quit the installation.This should  bring up the rest of the screen (with the menus, notification areas, panels etc.) . If it doesn't , you may have to boot the disc again and select "try ubuntu 10.10" or "try ubuntu without installing" or something like that.

When the normal screen appears, click System > Administration > Gparted partion editor. Then, you will see your NTFS partition, right click it and select resize.

Another dialog box will appear. Since you wanted to assign 12GB (the free space will be reduced to 7 - 8 GB once installed, so you might assign a little more), so 12GB = 12*1024 MB = 12288 MB, so drag the right side of the graph so that the partition measures 500118 - 12288 = 487830 MB.

Now click on the Apply Button (the button on the toolbar with the tick). Select Apply.

After Gparted has completed, click on Install Ubuntu 10.10 on the desktop.

If this brings you up to the graph, select the advanced mode.

Select the unallocated space from the list and click on the format tick box.

You can now proceed with the install.

---

### Post by abu46 on 2011-03-16
Herman's solution looks pretty good to me, having one single partition w\o worrying about separate partitions

can you elaborate about using swap file instead of swap partition, how to make one and of what size??

will swap file support sleep?

---

### Post by oldfred on 2011-03-16
I have never done a swap file. But this discusses it.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by abu46 on 2011-03-16
[B]finally installed ubuntu 10.10 for the first time in my life:D:D:D
used 1gb for swap and 11 for /, lets see how it pans out

this is my far "the" most helpful and responsive forum that i have came across on the web:D

experts like [COLOR="Red"]frogs hair[/COLOR] [/COLOR]& [COLOR="Red"]oldfred[/COLOR] along with fellow members like [COLOR="Red"]Hakunka-Matata[/COLOR]:P are always eager to help noobs like me 

thnx to all the guys who replied to my posts and helped me sort out my problems no matter how silly they were;)

lukin forward for a long stay here:D[/B]

---

### Post by oldfred on 2011-03-16
Glad you got it working. Happy Ubuntu-ing. :)

---

