---
title: "Partitions - take from Windows and give to Linux"
date: 2020-02-18
forum: Installation &amp; Upgrades
---

### Post by ewog on 2020-02-18
Good evening -

I'm running a Lenovo Flex 3 1480, dual boot with Win10 Home and Linux/Ubuntu 19.10.  Windows has ~800 gb of free/unused disk space, and Ubuntu is down to about 25mb free/unused disk space.  I would like to reduce the Windows partition and add the removed amount to Linux.  Thinking of removing 150 gb from Windows and adding it to Linux.  Here is what my disk looks like -  part way through you'll see text in _**[COLOR=#ff0000]red and underlined[/COLOR]**_, those are the two partitions I want to shrink/grow:

```
ktm@littleman:~$ sudo fdisk -l
[sudo] password for ktm: 
Disk /dev/loop0: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 54.66 MiB, 57294848 bytes, 111904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 149.93 MiB, 157192192 bytes, 307016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 89.9 MiB, 93417472 bytes, 182456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 91.32 MiB, 95748096 bytes, 187008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 44.9 MiB, 47063040 bytes, 91920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10SPCX-24H
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 32257289-B0D3-4D3A-9BAA-F79E10C5CE6E

Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1857079295 1856512000 _**[COLOR=#ff0000]885.3G Microsoft basic data[/COLOR]**_
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
/dev/sda6  1911556096 1951475711   39919616    19G Windows recovery environment
/dev/sda7  1951475712 1953523711    2048000  1000M Lenovo boot partition
/dev/sda8  1881229312 1903654911   22425600  _**[COLOR=#ff0000]10.7G Linux filesystem[/COLOR]**_
/dev/sda9  1903654912 1909508095    5853184   2.8G Linux swap
```

Partition table entries are not in disk order.


```
Disk /dev/loop8: 14.76 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 54.86 MiB, 57499648 bytes, 112304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 54.66 MiB, 57294848 bytes, 111904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 202.92 MiB, 212758528 bytes, 415544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 44.18 MiB, 46325760 bytes, 90480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 160.16 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 73.78 MiB, 77344768 bytes, 151064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 409.42 MiB, 429297664 bytes, 838472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 14.76 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 171.7 MiB, 180027392 bytes, 351616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ktm@littleman:~$ 
```


What would be the best way to achieve the 150 gb swap?  I'm fairly new to doing such things on a set-up system, but I have all my data backed up, so I can rebuild my partitions (Win10 and Ubuntu) if something goes south.

Thanks!

---

### Post by TheFu on 2020-02-18
Shrink sda3 from inside Windows however MSFT says to do it.

Because the 2 partitions are **NOT** next to each other, you can't "merge" the space into one, which is fine.  Normally, we want the OS partition to be 25G, then have other partitions mounted for other needs like /var and /home and /opt depending on the size needed.  If more flexibility is needed, then using LVM or some other advanced solution can make life easier.

After creating a partition the size you need, assuming you don't go with LVM, then **mkfs** to create a file system and mount it where needed.  Anything underneath that mount will not be available, so move any data to the new storage first.

BTW, would help if you edited the post above to remove all the "loop" entries.  They are not real storage and just clutter up the post, make it harder for people to see what's important.  Also, please post all command output wrapped in **code tags** so columns line up correctly. Easier posts to read get more help.  It is in the advanced editor (#).

```
lsblk -o name,size,type,fstype,mountpoint  |egrep -v squashfs  
```
would be helpful.

May want to make swap larger too, 4.1G.

---

### Post by ewog on 2020-02-19
Well, I know I wouldn't have come up with that string of commands for Terminal!  Thanks, and here's the output:
```

ktm@littleman:~$ sudo lsblk -o name,size,type,fstype,mountpoint  |egrep -v squashfs
[sudo] password for ktm: 
NAME     SIZE TYPE FSTYPE   MOUNTPOINT
sda    931.5G disk          
&#9500;&#9472;sda1   260M part vfat     /boot/efi
&#9500;&#9472;sda2    16M part          
&#9500;&#9472;sda3 885.3G part ntfs     
&#9500;&#9472;sda4  11.5G part ntfs     
&#9500;&#9472;sda5  1000M part ntfs     
&#9500;&#9472;sda6    19G part ntfs     
&#9500;&#9472;sda7  1000M part vfat     
&#9500;&#9472;sda8  10.7G part ext4     /
&#9492;&#9472;sda9   2.8G part swap     
ktm@littleman:~$ 
```

I understand I will shrink the MSFT partition from within Windows - going for 150 gb.  The next step is not clear to me.  I think the 150 gb space taken out of Windows will now just be un-noted disk space next to sda3.  So when I go to make a new partition (sda10 ?) I would make it (the 150 gb) of the same type as sda8 (part ext4   /)  Or would I create a partition that would replace the current undersized directory in Linux (i.e. /home  or /var?  I'll be doing some reading and research, but any guidance would be appreciated.

---

### Post by Impavidus on 2020-02-19
Your Ubuntu partition is very small. I wouldn't keep it even as a root partition. You could create a /home partition in de unallocated space after shrinking the Windows partition ([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)), but I suggest you delete all Ubuntu partitions (root and swap), use Windows tools to move sda4 to put it adjacent to sda5, then make a fresh Ubuntu install in the unallocated space. You can create a separate /home and swap partition, but neither of those are mandatory. Other partitions are rarely useful on a home system.

---

### Post by ajgreeny on 2020-02-19
As mentioned in Impavidus's post above you do not really have enough space for Ubuntu and as you've got presumably very little in the way of data in your Ubuntu partition ity may be easier to start againn with Ubuntu by shrinking your windows partition by as much as you can without inflicting any problems on its use due to lack of space for using that OS.

Then install Ubuntu again in the space you have made available.

It will be very useful to see a screenshot of gparted running if necessary from the live Ubuntu install system as that will show us where the current partitions are sited on disk and how much space may be available.

---

### Post by Dennis N on 2020-02-19
> The next step is not clear to me. I think the 150 gb space taken out of Windows will now just be un-noted disk space next to sda3. So when I go to make a new partition (sda10 ?) I would make it (the 150 gb) of the same type as sda8 (part ext4 /) Or would I create a partition that would replace the current undersized directory in Linux (i.e. /home or /var? I'll be doing some reading and research, but any guidance would be appreciated. 
MY easy solution would be to reduce sda3 as you planned, make a new ext4 partition in the resulting unallocated space, and use it as a separate data partition for Linux. Set it up to mount on startup in the /etc/fstab file of Linux and you can access your files from there. In particular, do you have media files? They often use a lot of space. Move them to the data partition. 

Example.
On this system&#8681;, the root is only 20 GB with 12 GB used, but there is a 85 GB data device mounted at /mnt/Common-Files that I use for my media and other data files. It is not a separate home partition - that still exists in skeleton form for the configuration files that many applications like to store there. (note: some devices in the display are LVM logical volumes - they could instead be partitions as you have). 
```
Filesystem                     Size  Used Avail Use% Mounted on
udev                           5.8G     0  5.8G   0% /dev
tmpfs                          1.2G  9.4M  1.2G   1% /run
/dev/mapper/os_vg2-umate_1604   20G   12G  6.3G  66% /
tmpfs                          5.9G  836K  5.9G   1% /dev/shm
tmpfs                          5.0M  4.0K  5.0M   1% /run/lock
tmpfs                          5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/sda1                       79M   25M   55M  31% /boot/efi
/dev/mapper/os_vg2-Common       85G   48G   33G  60% /mnt/Common-Files
tmpfs                          1.2G   36K  1.2G   1% /run/user/1000

```
Another advantage of this is when you have a multiboot system with several Linux, they can all mount the same data partition when they are running.

---

### Post by TheFu on 2020-02-19
Let's step back a bit.  When it comes to storage, there are 4 major ideas.

[LIST]
[*]    The disk
[*]    The partition - GPT allows 100+ primary partitions. MBR allows 4 primary partitions. Use GPT.
[*]    The file system - a file system must be put onto the partition. **mkfs** is the command. **mkswap** is used for swap.
[*]    The mount - generally, it is best to mount via the /etc/fstab configuration. Avoid any GUI.
[/LIST]

The disk holds partitions.
Partitions hold file systems. Files, directories are put onto file systems for our use.
File systems can be mounted to any directory, though it is best if the directory is empty.  As long as the directories and files appear in the correct places within the directory structure after mounted, then it will work fine.

Creating partitions inside a disk is pretty easy.  Use gparted or parted or fdisk or ... 
Creating an ext4 file system on a partition is pretty easy.   Use gparted or mkfs.

When doing partition work, it is usually easiest to boot from a Try Ubuntu flash drive, install gparted into the temporary environment, and do the partitioning and file system creating there.  Don't forget that sometimes deleting partitions, like swap, is the easiest way to get more space.  Recreating swap somewhere else, i.e. a new partition marked for swap use and formatted as swap, is really easy.

Then there's the hard part for most people - modifying the /etc/fstab.  An fstab is really a very bone head file.  It tells the OS at boot where to specific file systems AND how to use them.  That use is almost always for storage of files, but a swap partition is specified there usually as well.

Most fstab files have a little comment header to explain things. There are 6 columns required for each line. Each line describes how to mount a specific storage element, where to mount it, what type of file system it is, and any options.  The last 2 columns are for backup handling and when to check the mount for errors.
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
```
The full explanation is in the fstab manpage, with examples:
```
man -s 5 fstab 
```
It is usually easiest to modify an existing fstab rather than create a new one.  

A few tips when dealing w/ the fstab.
[LIST=1]
[*]always make a copy of the file before starting.  fstab.bak is a good name.
[*]use the sudoedit command for editing
[*]modify 1 line at a time, then test the results using **sudo mount -a**
[*]swap is not mandatory, but it is useful for a solid running system. When doing fstab maintenance, don't worry about swap. Just make certain it is there and working when you finish.
[*]Every non-comment line must have 6 columns.  1 or more spaces together creates a new column.
[*] line wrap will break an fstab. Don't let the editor do that.
[/LIST]
There aren't any GUI tools that I'd trust to modify an fstab correctly.

If this sounds too scary, might be best to free up the windows storage and do a fresh install into that storage using the "*Do something else*" option presented during all Ubuntu installations.

---

### Post by ewog on 2020-02-21
Good evening -
I've taken a couple steps and here are the results.  In Windows, I shrank the partition by 300 gb.  In Ubuntu, I downloaded Gparted and created a new partition, using the unallocated 300 gb from Windows.  Here is what the disk currently looks like:
```
ktm@littleman:~$ sudo fdisk -l
Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1242679295 1242112000 592.3G Microsoft basic data
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
/dev/sda6  1911556096 1951475711   39919616    19G Windows recovery environment
/dev/sda7  1951475712 1953523711    2048000  1000M Lenovo boot partition
/dev/sda8  1881229312 1903654911   22425600  10.7G Linux filesystem
/dev/sda9  1903654912 1909508095    5853184   2.8G Linux swap
/dev/sda10 1242679296 1857079295  614400000   293G Linux filesystem
ktm@littleman:~$ 

ktm@littleman:~$ sudo lsblk -o name,size,type,fstype,mountpoint  |egrep -v squashfs
NAME      SIZE TYPE FSTYPE   MOUNTPOINT
sda     931.5G disk          
&#9500;&#9472;sda1    260M part vfat     /boot/efi
&#9500;&#9472;sda2     16M part          
&#9500;&#9472;sda3  592.3G part ntfs     
&#9500;&#9472;sda4   11.5G part ntfs     
&#9500;&#9472;sda5   1000M part ntfs     
&#9500;&#9472;sda6     19G part ntfs     
&#9500;&#9472;sda7   1000M part vfat     
&#9500;&#9472;sda8   10.7G part ext4     /
&#9500;&#9472;sda9    2.8G part swap     
&#9492;&#9472;sda10   293G part ext4     
ktm@littleman:~$ 
```

So I see a few of the next steps are to create a mount point for /dev/sda10, create a new entry in the /etc/fstab file, and somehow swap my current Ubuntu set-up on /dev/sda8 to /dev/sda10.  I'm fine losing the 11 gb of the current Ubuntu partition as I don't see my keeping this laptop long enough to use up the 1 tb drive.  And if I should need to add space, there are still a few hundred gb in Windows to steal.  I also know I'll need to update the boot registry to point to Linux on the new partition.

I'm feeling comfortable with creating the mounting point and editing the /etc/fstab file.  It's moving my current configuration from /dev/sda8 to /dev/sda10 that has me worried.  I'd rather not deal with re-installing some specific software and going through the hassles of de-registering it, then having to re-register after it's loaded onto /dev/sda10.  I checked with StorageCraft, and they don't have any software compatible with Ubuntu 19.10 (they're only confident to 16.04).  I'm not sure of any other image/hard drive back-up software.  I've used StorageCraft for 7 or 8 years at work, and have full confidence from those experiences, so have not tested any others.

Thanks for any advice!

---

### Post by TheFu on 2020-02-21
This order, which I manually created based on the partition "Start" sector, 
```
$ sudo fdisk -l
Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1242679295 1242112000 592.3G Microsoft basic data
**/dev/sda10 1242679296 1857079295  614400000   293G Linux filesystem**
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
/dev/sda8  1881229312 1903654911   22425600  10.7G Linux filesystem
/dev/sda9  1903654912 1909508095    5853184   2.8G Linux swap
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
/dev/sda6  1911556096 1951475711   39919616    19G Windows recovery environment
/dev/sda7  1951475712 1953523711    2048000  1000M Lenovo boot partition

```
is more useful.  See how the start locations are in order?  We can see the partition layout on the disk this way.

Ok, so sda10 is too large.  Too small or too large are both mistakes.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has a layout w/ explanations for _why_ the different storage areas should be sized in specific ways.  For typical desktop users, those sizes are close enough.  A software developer or someone running network services for a subnet could need different sizes. The software development tools make a difference based on many factors and the languages needed.

I need to say, I would not be doing this the way you are.  I would backup any data, settings, and a list of installed applications for easy re-install after I did a clean, fresh, install into free space.  My install would be a minimal version of the same release/flavor I am currently running.  The "do something else" option for storage/instal would be selected.  [https://ubuntuforums.org/showthread.php?t=2436006&highlight=remove-older-than](https://ubuntuforums.org/showthread.php?t=2436006&highlight=remove-older-than) shows how I would do it for a simple setup.  YMMV.  Lots of discussion/**why** in that thread about sizes for different parts of any desktop Linux install. It doesn't need to be too complicated, but creating 3-4 storage areas at install time can really make upgrades easier in the future.

Here's someone who I think is doing excellent backups: [https://ubuntuforums.org/showthread.php?t=2422831](https://ubuntuforums.org/showthread.php?t=2422831)  He uses LVM and LVM-snapshots which adds some capabilities and complexity to storage management.  For a typical desktop, LVM complexity probably isn't worth it, but when you don't know how much storage you need assigned to the OS, addons, HOME, and work areas, LVM provides incredible flexibility. 

**Optional LVM stuff ... **
After you backup everything you don't want to lose, you could convert sda10 into an LVM PV, add sda8 into another LVM PV, merge both into a single VG, then slice out parts of the storage using LVs as needed, where needed.  The real trick to getting the best flexibility from LVM is never fully allocate all the storage.  Reducing the size of an LV or partition is a hassle, but increasing the size of an LV is 5 seconds AND the system can keep running and remain in use while this happens.  
Swap can be an LV, so you can delete sda8 and sda9, then merge that storage into a single partition, mark is as an LVM-PV, add it to the VG and have LV storage automatically come from it.  
Where the current swap is located (sda9), I'd make that into /boot. Ubuntu can't boot from LVM storage today, so the boot storage needs to be a regular partition. If you don't want  to waste any storage, /boot needs to be 600MB-1GB in size.  

If you could move sda4 somewhere else, that certainly would simplify your storage layout. Then all the Linux stuff could be contiguous.

Clear as mud?

---

### Post by ewog on 2020-02-22
The Fu -  thanks for all the good advice, and the links to additional info.  Will be doing some reading and planning.

Have also considered this approach to the machine.  Since the Windows side doesn't have info I really need (all of it is on an external hard drive), and the Ubuntu side is new and in a similar state, maybe I should just wipe the whole drive, reload Windows into the partition size I want (leaving most of the disk free), then reload Ubuntu into the free space.  This should realign the partitions as you suggested - all Windows/Lenovo next to each other, then Ubuntu in its own space, some free disk space left to play with, etc.  Might be the easiest and cleanest way to accomplish the final goal.

---

### Post by TheFu on 2020-02-22
IDK.  Lenovo probably installed some stuff on the storage and moving those may break them.
You have this:
```
$ sudo fdisk -l
Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1242679295 1242112000 592.3G Microsoft basic data
/dev/sda10 1242679296 1857079295  614400000   293G Linux filesystem
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
/dev/sda8  1881229312 1903654911   22425600  10.7G Linux filesystem
/dev/sda9  1903654912 1909508095    5853184   2.8G Linux swap
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
/dev/sda6  1911556096 1951475711   39919616    19G Windows recovery environment
/dev/sda7  1951475712 1953523711    2048000  1000M Lenovo boot partition
```

If you stay with partitions and leave the non-Linux stuff alone but delete all the linux partitions, 
```
$ sudo fdisk -l
Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System (mount to /boot/efi should be FAT32 already)
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1242679295 1242112000 592.3G Microsoft basic data
**/dev/sda?      E-M-P-T-Y  - 293G**
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
**/dev/sda?          E-M-P-T-Y    ~13.5G Linux**
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
/dev/sda6  1911556096 1951475711   39919616    19G Windows recovery environment
/dev/sda7  1951475712 1953523711    2048000  1000M Lenovo boot partition
```

I'd want this (removed stuff we don't touch): 
```

/dev/sda3      567296 1242679295 1242112000 592.3G Microsoft basic data
**/dev/sda?       1G /boot/  ext2 **
**/dev/sda?      25G for /   ext4 **
**/dev/sda?      25G for /home   ext4 ** - perhaps larger if you do java coding. Other languages don't need more storage.
**/dev/sda?          E-M-P-T-Y    ~244G Linux for use later** OR use for temporary media files?
/dev/sda4  1857079296 1881227762   24148467  11.5G Microsoft basic data
**/dev/sda?        4.1G Linux swap**
**/dev/sda?          E-M-P-T-Y    ~9.4G Linux for use later** (not really sure how to use this without LVM); perhaps for NTFS shared data?
/dev/sda5  1909508096 1911556095    2048000  1000M Windows recovery environment
```

Set that up during the Ubuntu install under the "do something else" option for storage/partitioning.
If you want encryption, using LVM makes it easier.  The only time I messed with manual encryption setup, I had to use GB vs GiB math to get the different pieces inside each other.  I'm positive at least 10G was wasted.

If you know what sda4 holds and can move it somewhere else - either to the end or next to sda3, then you'd have contiguous space for Linux.

If you go with a manual LVM setup, the locations just don't matter.  Any storage on sda (the HDD) can be merged together so you don't need to worry about slices at all.  To you, once PVs and the VG are setup, you'd just create LVs and they'd put storage from the single VG as needed.  For almost all purposes, an LV can be thought of as a partition that can be extended while live without  any regard to the underlying physical storage layout. Obviously, once the VG storage has been 100% allocated, we lose lots of flexibility.  OTOH, moving LVM to a larger disks is just 1 command per PV.  Or if you like to live dangerously, you can add a new PV from the new disk to the existing VG and blindly start expanding LVs as you like.  This is dangerous, since a failure of ether disk will almost certainly cause data loss and probably corrupt the entire VG and LVs involved.  Back in 2002, I lost all the data on 3 HDDs because 1 failed, but I'd expanded LVM across all three physical disks.  I didn’t have backup religion back then.

Only you know what makes sense for your system, current skill level, etc.  OTOH, if you try this and it doesn't work, what has been lost besides time? You could still wipe Windows and reinstall, then install Linux, right?  I haven't installed Windows since around 2008-ish. Did they finally allow control over partition sizing and do they recognize non-NTFS, non-FAT, partitions and leave them alone?

---

