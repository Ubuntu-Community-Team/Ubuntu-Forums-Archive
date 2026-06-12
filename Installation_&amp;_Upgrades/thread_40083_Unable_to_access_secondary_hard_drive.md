---
title: "Unable to access secondary hard drive"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by andshewas on 2005-06-07
Hiya.

I just installed the 5.04 Ubuntu.  I'm new to linux...was a windows user until the last virus.  I installed a bunch of different versions of linux and I've found Ubuntu to be the perfect one, except for one problem: I cannot access my secondary hard drive.  I'm sure I'm just linux-illiterate, and it's actually under my nose, here...but I've not been able to find it in the Computer or Home sections.  In the device manager, however, it is listed.  I just don't know how to access it.  If anyone can direct me to some instructions (which I've been searching for all day!!) or give a few pointers, I'd be forever grateful!  

Thanks

---

### Post by mingus on 2005-06-07
Starting with the basics, is the drive mounted?  If it has, then you should be able to go to:
Applications/System Tools/File Browser
and on the panel to the left choose "Tree" and then click on Filesystem.  You should find the directory you mounted to, click on that and you should see the files.

If "mount" doesn't mean anything to you yet, then do this:

Applications/System Tools/Terminal
$sudo fdisk -l
this will display all of your drives and partitions; copy/paste to this thread

$cat /etc/fstab
(be sure the terminal screen is stretched wide so the text doesn't wrap).  Copy/paste here.  This tells the kernel what to mount when you boot.

$cat /etc/mtab
again, copy/paste here.  This tells what has actually been mounted.

The data is the starting point to determine why it isn't being mounted.

---

### Post by andshewas on 2005-06-07
Thank you so much for such a quick response!  I pasted the commands you told me to and here is the result of all three commands:
chicken@chicken:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9538    76613953+  83  Linux
/dev/hda2            9539        9726     1510110    5  Extended
/dev/hda5            9539        9726     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12516   100534738+   7  HPFS/NTFS
/dev/hdb2           12517       24792    98606970    f  W95 Ext'd (LBA)
/dev/hdb5           12517       24792    98606938+   7  HPFS/NTFS
chicken@chicken:~$ $cat /etc/fstab
bash: /etc/fstab: Permission denied
chicken@chicken:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
chicken@chicken:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
chicken@chicken:~$


To reduce confusion, yes, I'm a dork, and my computer's name is chicken.  I'm not really sure what it means to mount the drive.  I heard that was what I had to do, but I hadn't a clue where to start.  I have two drives installed in the computer.  My main drive (on which Ubuntu is installed) is an 80g drive.  The other drive is a 250g drive that is separated into two partitions.  Both are full with all my files from when I had windows, so I'm praying nothing happened to the drive.  So what does the code above tell me?  I can understand that it is showing the main boot drive and two other drives (I'm guessing the two partitions on my slave drive.) but I'm not sure what I must do.  

I appreciate your help so much.  Thanks!

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=andshewas]Thank you so much for such a quick response!  I pasted the commands you told me to and here is the result of all three commands:
chicken@chicken:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9538    76613953+  83  Linux
/dev/hda2            9539        9726     1510110    5  Extended
/dev/hda5            9539        9726     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12516   100534738+   7  HPFS/NTFS
/dev/hdb2           12517       24792    98606970    f  W95 Ext'd (LBA)
/dev/hdb5           12517       24792    98606938+   7  HPFS/NTFS
chicken@chicken:~$ $cat /etc/fstab
bash: /etc/fstab: Permission denied
chicken@chicken:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
chicken@chicken:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
chicken@chicken:~$


To reduce confusion, yes, I'm a dork, and my computer's name is chicken.  I'm not really sure what it means to mount the drive.  I heard that was what I had to do, but I hadn't a clue where to start.  I have two drives installed in the computer.  My main drive (on which Ubuntu is installed) is an 80g drive.  The other drive is a 250g drive that is separated into two partitions.  Both are full with all my files from when I had windows, so I'm praying nothing happened to the drive.  So what does the code above tell me?  I can understand that it is showing the main boot drive and two other drives (I'm guessing the two partitions on my slave drive.) but I'm not sure what I must do.  

I appreciate your help so much.  Thanks![/QUOTE]
 "Mounting" means making contetns of a disk available as part of your filesystem. Think of it as software version of "connecting" a drive to the computer. 

File /etc/fstab contains ifnormation about the disks (and other devices) that are mounted at boot time. E.g., line
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
means "mount device /ddev/hda1 (this is firts partition of firtst harddrive), which has filesystem of type ext3, as directory / ."

Thus, what you need is to add simialr line in fstab for each of the partitions of your second harddrive (hdb). According to output of fdisk, you have 3 partitions /dev/hdb1, /dev/hdb2, and /dev/hdb5. So add a line for each of them to /etc/fstab, e.g. 
/dev/hdb1 /media/disk2 ntfs umask=0222 0 0 
(see [http://ubuntuguide.org/#windows)](http://ubuntuguide.org/#windows)). Instead of /media/disk2, you can use any directory name - but it must laready exist and be empty. Use different names for different drives/partitions.

---

### Post by mingus on 2005-06-08
A couple of additions to Alexander's reply . . .

You do not want to put /dev/hdb2 in your fstab file.  It appears that the second data partition hdb5 was created as a logical inside of an extended (hdb2), rather than as its own second primary.  So hdb1 and hdb5 are the only actual data partitions.

As far as the directory that you mount them in, that depends on how you want to see them in your filesystem (like Windows Explorer).  You can add directories to /media as Alexander shows, or you can create top level directories with whatever english syntax you want.  Go to Applications/System Tools/Terminal, and do
$cd /
$sudo mkdir  <directoryname1>
$sudo mkdir  <directoryname2>
$sudo gedit /etc/fstab
this will open fstab in a text editor - after the hda5 line add something like:
/dev/hdb1    /<directoryname1>    ntfs     defaults       0   0
/dev/hdb5    /<directoryname2>    ntfs     defaults       0   0
save the file and exit
reboot

now go to Places/Home.  In the upper left column click the tab and click on "tree", now click on filesystem.  You should see the 2 new directories, click and you should see your files.

If you don't see the directories, in the terminal again do
$cat /etc/mtab
to see everything that is mounted.  If the directories are not there, something failed.

Because the partitions are NTFS, you only have read access, so you cannot modify these files from Ubuntu.  I understand there is software now that can enable this, but I haven't tested it.  If these are primarily data files and you aren't using Windows to change that data a lot, you can consider converting the partitions to FAT32 which would permit write access from Ubuntu.  Conversion is done with a 3rd party partitioning tool in Windows like PartitionMagic.

This should do the trick.

---

