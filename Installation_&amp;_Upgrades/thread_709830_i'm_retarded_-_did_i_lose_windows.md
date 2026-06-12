---
title: "i'm retarded - did i lose windows?"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by davesec on 2008-02-27
hi!

i think i'm going to switch to ubuntu, so i installed it. i made a new partition for it and a swap partition. then when i booted up, it went straight into ubuntu (no choice in grub for windows xp). i found a thread here explaining what to do if grub doesn't recognize windows xp, and it involved finding out what disk windows was on, and it seemed like windows should be on a disk called sda1/2/3.. when i type in fdisk -l in terminal all i can see are sda1/sda2 which are those two partitions i made.. nothing about a disk for windows.

is windows xp still on the main /dev/sda? when i went through the install process it showed that there was 60gb free space on the hard disk. i know windows wasn't using up more than 20gb of this with my files, so i allocated only 10gb for ubuntu and 500mb for the swap. 

so did i ruin things, or is xp still lurking around somewhere on my harddrive? if it is, how to i load into it?

if all is lost, the main things i wanted to keep windows for are skype calls - i noticed there's some sort of phone application installed on this computer, but i was wondering if anyone knows if you can make calls to people using skype (i'm sure i can figure this out). i also have a motu traveller sound card/preamp which runs via a firewire connection - i keep reading that motu and ubuntu don't like each other, but it would rule if i could get that thing to work on this machine.

thanks guys!
dave

---

### Post by uberlube on 2008-02-27
you do realize that ubuntu needs an ext3 partition to run right. So if you had 60 gigs of free diskspace that was still on the windows NTFS partition you would have had to resize the NTFS and create a ext3 partition with the unused space.

---

### Post by uberlube on 2008-02-27
and you can also use skype in linux

---

### Post by uberlube on 2008-02-27
use the synaptic package manager to install it and your good to go

---

### Post by davesec on 2008-02-27
hi,

i'm aware i needed to create a ext3 partition, and assumed the partitioning program that was on ubuntu would shrink the harddrive accordingly and then use the free space as ext3. i guess what i'd like to know is whether or not that means windowsxp is gone or not. does the 10gb i allocated come from unused free space on the ntfs partition, or does it just take space from it at random or what.

i'm totally new to this, sorry about all the questions. downloading skype right now - one issue soon to be resolved.

thanks!

---

### Post by dstew on 2008-02-27
> when i type in fdisk -l in terminal all i can see are sda1/sda2 which are those two partitions i made.. nothing about a disk for windows.Windows is probably gone. Post the output of **sudo fdisk -l** so we can see the partitions that remain to be sure.

---

### Post by davesec on 2008-02-27
hey! here's what pops up from sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x881e3473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1277      489982+  82  Linux swap / Solaris

---

### Post by patrickaupperle on 2008-02-27
It looks like windows is gone, but I am new to this, too.

---

### Post by davesec on 2008-02-27
well, if it's indeed gone, then the direction of this thread can move to getting ubuntu to recognize the maxtor external harddrive where all my stuff is backed up. i popped in the usb cord and nothing has happened thus far. i'm doing some preliminary reading and it would appear that there could be some issues if the harddrive is formatted as ntfs?!

looks like i have made some poor choices in the last few days...

also, if windows is really gone, is there an easy way to allocate the remaining free space to the current partition ubuntu is on? if windows isn't there, i might as well make use of the other 45+gb floating around on my harddrive.

thanks!

also - and this is a long shot, is there a program that will allow you to import cubase sx3 files into whatever popular ubuntu daw exists?!

---

### Post by dstew on 2008-02-27
> is there an easy way to allocate the remaining free space to the current partition ubuntu is on?You can expand/move partitions using gparted. However, you have to work on an unmounted disk, so you will need to use the [gparted live CD]("http://gparted-livecd.tuxfamily.org/") rather than using gparted from your hard disk ubuntu system.

---

### Post by davesec on 2008-02-27
sounds good

i guess i can always just reinstall xp as well.. should i be able to do this and keep ubuntu running on its current partition? (i've only used this system since yesterday but i like it so far)

---

### Post by davesec on 2008-02-27
also, if my external harddrive is indeed formatted as ntfs, is there any way at all i can access the files/work on it through ubuntu?

---

### Post by Virtualboxbuntu on 2008-02-27
Check out this website: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")
You should be able to access an NTFS drive. It isn't perfect, though.

---

### Post by davesec on 2008-02-27
hey! i checked out the website and installed ntfs config. it seems to be installed correctly. however when i open it up and type in my password, i don't get that 'the following partitions were detected and can be configured'. instead it just jumps to the screen that says 'NTFS write support configuration tool'. the only option i can click on is 'enable write support for external drive', which seems okay because i only have an external drive. so i click okay and the screen disappears. apparently at this point i should now see a mount point on my desktop, but i don't. there's nothing there. i checked out file browser and don't see anything there either. device manager still shows that there's a mass usb storage device.

any suggestions?!

thanks!
dave

---

### Post by froy02 on 2008-02-28
Post the contents of your /etc/fstab file and the results of the command from terminal of:
code:
sudo fdisk -l

---

### Post by davesec on 2008-02-28
etc/fstab:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=0b05bed5-217e-4175-b9b3-e411ceb3d459 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=9d306e5e-5216-49e1-ba68-f8319a36881b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

there's also a fstab.pre-ntfs-config file in /etc, for what it's worth.

sudo fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x881e3473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1277      489982+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e227b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6375    51199155    f  W95 Ext'd (LBA)
/dev/sdb2            6376       19123   102398310    7  HPFS/NTFS
/dev/sdb3           19124       30401    90590535    7  HPFS/NTFS
/dev/sdb5               2        6375    51199123+   7  HPFS/NTFS


thanks!

---

### Post by davesec on 2008-02-28
bump!

---

### Post by froy02 on 2008-02-28
Okay, here's what I see in your hard drive configuration: You have linux installed in 60 gb hard drive (sda) and you have an 250 gb external hd with 3 partitions (sdb).

Please note that /dev/sdb1 is the same as /dev/sdb5. They have the start and end blocks.

Add the following 3 lines to your fstab file.

/dev/sdb2 /media/disk1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb3 /media/disk2 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb5 /media/disk3 ntfs-3g defaults,locale=en_US.UTF-8 0 0

Hope this helps you mount that drive.

---

