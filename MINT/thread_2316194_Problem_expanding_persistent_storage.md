---
title: "Problem expanding persistent storage"
date: 2016-03-05
forum: MINT
---

### Post by michael358 on 2016-03-05
Hi

I have installed Lubuntu 14.04.3 on 2 16GB flash drives. I used Pendrivelinux and created a 2GB persistant volume during creation.  I am running Lubuntu on drive A while trying to change partitions on drive B. I followed the instructions on the Pendrivelinux page, but had a problem right away. I have searched high and low and not seen the same problem anywhere.

First I deleted the casper-rw file, then used Gparted to unmount the partition on drive B. I then resize the original partition and try to create a new partition with the "unallocated space" left over. I get an error that says "cannot create more than one primary partition". Error message recommends creating an extended partition, then partitions inside that. When I try to delete the existing partition, which is listed as the first step, Gparted crashes, or seems to delete the primary partition (after I click on the check mark, to execute the operation) but the partition just reappears somehow.

Help please?

---

### Post by sudodus on 2016-03-06
Welcome to the Ubuntu Forums :-)

I think your problem is similar to what is discussed in the following thread: [live usb not work with persistent partition](http://ubuntuforums.org/showthread.php?t=2315728)

***Please read the conversation (in that thread), and then come back and tell us how you want to continue.***

> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

1. Is it enough to get a persistent live drive drive of an Ubuntu flavour, ToriOS or Debian Jessie, or

2. are you trying with another linux distro, or do you want help to fix the system you have, so that it works?

-o-

***If 1:*** Try another tool, which creates persistence with a partition automatically, ***mkusb***. It works with the Ubuntu flavours, with ToriOS and with Debian Jessie. See the following links

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

-o-

***If 2:*** It looks like you have done things correctly. But there is some detail, that is wrong.

***What linux distro and version*** are you trying to make persistent live?

*You* told us already: Lubuntu 14.04.3
> 
Post the ***output of the following commands*** in a terminal window, when booted live-only from the USB drive

```
df
```
```
sudo parted -ls
```
```
sudo lsblk -fm
```

Put the output within [noparse]```
tags
```[/noparse] to make it easier to read :-)

---

### Post by michael358 on 2016-03-07
Hi

I just re-read my question and it looks like I did not explain myself well at all. I used Pendrivelinux (and I tried Unetbootin) to first create USB live Linux with persistant storage. I wanted to create a 10GB persistent volume on the same USB the Linux boots from.

I haven't had any problems getting a 4GB persistent volume to work, but when I try to do this  [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/) I haven't made it past trying to create the 10GB casper-rw partition. 

I have decided to try using Linux Mint, and will try the commands you suggested once I get it running.

---

### Post by michael358 on 2016-03-07
I now have Linux Mint 17.3 Cinnamon. Works well, and I have installed VM to test persistence. It is running on a 8GB USB drive. I also created a live USB with a 16GB USB drive. Both have a persistent volume created with Pendrivelinux. I just tried to re size the partition on the 16GB drive and had a little more success. GParted let me resize the original primary partition, create another primary 12GB partition. But when I try to execute both operations GParted crashes every time. When I try to do the operations one at a time, re sizing the original partition, I get an error to check for bad sectors. I don't have another USB Drive to test if the problem is with the drive or it is something else. 

Here is the output from the commands

```
mint@mint ~ $ dfFilesystem     1K-blocks    Used Available Use% Mounted on
/cow             4055872 2075172   1771344  54% /
udev             2985984      12   2985972   1% /dev
tmpfs             599496    1616    597880   1% /run
/dev/sdc1        7548624 5730160   1818464  76% /cdrom
/dev/loop1       1499392 1499392         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            2997476       4   2997472   1% /tmp
none                5120       0      5120   0% /run/lock
none             2997476     672   2996804   1% /run/shm
none              102400      28    102372   1% /run/user
/dev/loop0       4055872 2075172   1771344  54% /media/mint/casper-rw
/dev/sde        15171584      16  15171568   1% /media/mint/UUI



```



```
mint@mint ~ $ sudo parted -lsModel: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   fat32        EFI system partition          boot
 2      316MB   1259MB  944MB   ntfs         Basic data partition          hidden, diag
 3      1259MB  1394MB  134MB                Microsoft reserved partition  msftres
 4      1394MB  201GB   200GB   ntfs         Basic data partition          msftdata
 5      201GB   479GB   277GB   ntfs         Basic data partition          msftdata
 6      479GB   500GB   21.5GB  ntfs         Basic data partition          hidden, diag




Model: ATA KINGSTON SMSM150 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  6443MB  6442MB               Basic data partition  hidden
 1      6445M
```

[CODEmint@mint ~ $ sudo lsblk -lslsblk: invalid option -- 's'


Usage:
 lsblk [options] [<device> ...]


Options:
 -a, --all            print all devices
 -b, --bytes          print SIZE in bytes rather than in human readable format
 -d, --nodeps         don't print slaves or holders
 -D, --discard        print discard capabilities
 -e, --exclude <list> exclude devices by major number (default: RAM disks)
 -f, --fs             output info about filesystems
 -h, --help           usage information (this)
 -i, --ascii          use ascii characters only
 -m, --perms          output info about permissions
 -l, --list           use list format ouput
 -n, --noheadings     don't print headings
 -o, --output <list>  output columns
 -P, --pairs          use key="value" output format
 -r, --raw            use raw output format
 -t, --topology       output info about topology


Available columns:
       NAME  device name
      KNAME  internal kernel device name
    MAJ:MIN  major:minor device number
     FSTYPE  filesystem type


[/CODE]

---

### Post by howefield on 2016-03-07
Moved to the "*MINT*" forum.

---

### Post by sudodus on 2016-03-07
> **michael358 said:**
> I now have Linux Mint 17.3 Cinnamon. Works well, and I have installed VM to test persistence. It is running on a 8GB USB drive. I also created a live USB with a 16GB USB drive. Both have a persistent volume created with Pendrivelinux. I just tried to re size the partition on the 16GB drive and had a little more success. GParted let me resize the original primary partition, create another primary 12GB partition. But when I try to execute both operations GParted crashes every time. When I try to do the operations one at a time, re sizing the original partition, I get an error to check for bad sectors. I don't have another USB Drive to test if the problem is with the drive or it is something else. 

Here is the output from the commands

```
mint@mint ~ $ dfFilesystem     1K-blocks    Used Available Use% Mounted on
/cow             [COLOR="#0000FF"]4055872[/COLOR] 2075172   1771344  54% /
udev             2985984      12   2985972   1% /dev
tmpfs             599496    1616    597880   1% /run
/dev/sdc1        7548624 5730160   1818464  76% /cdrom
/dev/loop1       1499392 1499392         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            2997476       4   2997472   1% /tmp
none                5120       0      5120   0% /run/lock
none             2997476     672   2996804   1% /run/shm
none              102400      28    102372   1% /run/user
/dev/loop0       [COLOR="#0000FF"]4055872[/COLOR] 2075172   1771344  54% /media/mint/casper-rw
/dev/sde        15171584      16  15171568   1% /media/mint/UUI

```
Persistence is working here (but 'only' with a file)> 

```
mint@mint ~ $ sudo parted -lsModel: ATA Hitachi HTS54505 (scsi)
...
Model: ATA KINGSTON SMSM150 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  6443MB  6442MB               Basic data partition  hidden
 1      6445M
```

```
mint@mint ~ $ sudo lsblk -ls
lsblk: invalid option -- 's'
```
Sorry, I was in a hurry and supplied the wrong options (those for parted), it should be

```
[SIZE=3]sudo lsblk -fm[/SIZE]
```
Make the terminal window wide when you run it (to avoid line wrapping).

> When I try to do the operations one at a time, re sizing the original partition, I get an error to check for bad sectors. I don't have another USB Drive to test if the problem is with the drive or it is something else. 

Maybe your problem is that there are bad sectors on the pendrive. Maybe it is only some corruption of the partition table or file system.

But I suggest that you start all over with that pendrive. [Wipe the whole device with mkusb](https://help.ubuntu.com/community/mkusb/wipe). If that works, fine, if not, I think you will find out where the bad sectors start, and you can try to use the part of the drive 'before' the start of bad sectors.

---

### Post by michael358 on 2016-03-08
I wiped the drive with MKUSB, reinstalled Cinammon, but that didn't do it. 

I decided to try Xfce instead because I thought maybe my computer is underpowered for Cinammon. I also went out and bought 2 new 16GB pen drives, and did a clean install on my computer. I have been formatting all these drives with Windows, and using Pendrivelinux and Unetbootin on Windows...thought a clean install would help. My next step is trying MKUSB to create 2 live USB's.

I just got the same result. GParted lets me resize the original primary partition and add another one I label "casper-rw". When I try to execute the operations GParted crashes. Here is the output of the same code from before.

```
NAME   FSTYPE   LABEL     MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                  sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat     SYSTEM               &#9500;&#9472;sda1   300M root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs     Recovery             &#9500;&#9472;sda2   900M root  disk  brw-rw----
&#9500;&#9472;sda3                               &#9500;&#9472;sda3   128M root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs     OS                   &#9500;&#9472;sda4 186.3G root  disk  brw-rw----
&#9500;&#9472;sda5 ntfs     DATA                 &#9500;&#9472;sda5 258.2G root  disk  brw-rw----
&#9492;&#9472;sda6 ntfs     Restore              &#9492;&#9472;sda6    20G root  disk  brw-rw----
sdb                                  sdb     22.4G root  disk  brw-rw----
&#9500;&#9472;sdb1                               &#9500;&#9472;sdb1  16.4G root  disk  brw-rw----
&#9492;&#9472;sdb2                               &#9492;&#9472;sdb2     6G root  disk  brw-rw----
sdc                                  sdc     14.6G root  disk  brw-rw----
&#9492;&#9472;sdc1 vfat     UUI       /cdrom     &#9492;&#9472;sdc1  14.6G root  disk  brw-rw----
sdd                                  sdd     14.6G root  disk  brw-rw----
&#9492;&#9472;sdd1 vfat     UUI                  &#9492;&#9472;sdd1  14.6G root  disk  brw-rw----
loop0  ext2     casper-rw            loop0      4G root  disk  brw-rw----
loop1  squashfs           /rofs      loop1    1.4G root  disk  brw-rw----

```

```
mint@mint ~ $ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             4055872   66080   3780436   2% /
udev             2985988      12   2985976   1% /dev
tmpfs             599496    1612    597884   1% /run
/dev/sdc1       15256560 5709920   9546640  38% /cdrom
/dev/loop1       1475328 1475328         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            2997476      12   2997464   1% /tmp
none                5120       0      5120   0% /run/lock
none             2997476      84   2997392   1% /run/shm
none              102400      28    102372   1% /run/user
mi
```


```
mint@mint ~ $ sudo parted -ls
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   fat32        EFI system partition          boot
 2      316MB   1259MB  944MB   ntfs         Basic data partition          hidden, diag
 3      1259MB  1394MB  134MB                Microsoft reserved partition  msftres
 4      1394MB  201GB   200GB   ntfs         Basic data partition          msftdata
 5      201GB   479GB   277GB   ntfs         Basic data partition          msftdata
 6      479GB   500GB   21.5GB  ntfs         Basic data partition          hidden, diag


Model: ATA KINGSTON SMSM150 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  6443MB  6442MB               Basic data partition  hidden
 1      6445MB  24.0GB  17.6GB               HFS


Model: SanDisk Cruzer Switch (scsi)
Disk /dev/sdc: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  15.6GB  15.6GB  primary  fat32        boot, lba


```

---

### Post by sudodus on 2016-03-08
At this point I have one question about ***gparted***: Are you trying to edit a partition that is used by the running operating system?

You should boot into one system (for example a live system in one pendrive) and edit partitions of another system, in another pendrive. If those partitions were auto-mounted, you should unmount them before starting to edit.


And I have one question about ***mkusb***: Did you try to make a persistent live drive with mkusb? In that case, please describe with as much details as possible. What happened? How did it go wrong?


Finally, please describe ***your computer***,

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

I guess it is running in UEFI mode (and mkusb should be able to make pendrives for you that work in UEFI mode).

---

### Post by michael358 on 2016-03-08
Pardon the double post. I should have looked closer at Sudodus post #2. Correct, my problem was similar to the other thread, and I think I just managed to create a live USB with a 10GB persistent volume using MKUSB (as you suggested). Thanks for the help!!!

---

### Post by sudodus on 2016-03-08
I'm glad it works for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

