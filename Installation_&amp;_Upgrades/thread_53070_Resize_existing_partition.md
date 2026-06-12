---
title: "Resize existing partition?"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by CrazyDesi on 2005-07-30
I have a Windows partition in /dev/hda2/ is there a way to resize some of it to a Linux partition or to write directly on it(which I'v read is apparently unsafe).  Anyone know a good program and can help a linux newbie in doing the steps required?

---

### Post by heimo on 2005-07-30
If it's ntfs, reading is possible, writing unsafe (and not directly supported by default Ubuntu kernels), if it's fat, it's possible to both read and write. What you need to do is mount the drive (I don't know how to do it using GUI), in shell/terminal using something like
 ```
mkdir /media/windrive (creates mountpoint, only needed once)
mount /dev/hda2 /storage/windrive (does the actual mounting)

``` 
If this is successfull, you can later add it to /etc/fstab (man fstab). You may need to use -t flag with mount command to spesify filesystem type, ie. -t vfat or -t ntfs

For repartitioning, check gparted
 ```
sudo apt-get install gparted
sudo gparted

``` 
Haven't used it really, so I don't know if it's enough for you, but it can resize partitions.

EDIT: edited mkdir line

---

### Post by egilj on 2005-07-30
I resized on my laptop using the Knoppix 3.9 live-CD and QT-parted. You can do the same with other live-CD distributions.

---

### Post by CrazyDesi on 2005-07-30
Alright I actually got it to the point that there is free space on my hard drive.  Is there a way to make the free space allocated to the Linux partition I already have?

---

### Post by heimo on 2005-07-30
Maybe. :) If you have anything valuable on that disk, I'd make backup now (if you haven't already).

Couple links that can be useful:
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC30](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC30)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by CrazyDesi on 2005-07-30
Ok I am confused out of my mind this is how parted shows up my hard drive can anyone tell me how to put the freespace to my ext3 partition?

(parted) print
Disk geometry for /dev/hda: 0.000-76319.085 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031     47.065  primary   fat16
2         47.065  47732.189  primary   ntfs        boot
4      62236.187  72425.852  extended
7      62244.062  62895.102  logical   linux-swap
5      62895.133  72002.263  logical   ext3
6      72002.294  72425.852  logical   linux-swap
3      72425.852  76316.594  primary   fat32

---

### Post by heimo on 2005-07-30
Well... I don't know how to do it in parted, but could the solution be to boot into windows, copy the stuff on fat32-partition to the large ntfs partition, boot into linux or live CD, remove the second swap, remove the fat32, grow the partition*, create the second swap (if neccessary), create new smaller fat32 partition and copy the stuff back (in Windows) from ntfs partition?

Maybe I missed something (or don't know all the relevant information), but that's what came to my mind.


*) in gparted or qtparted (this should be possible when you have free space just after the partition)

---

### Post by CrazyDesi on 2005-07-30
K I dont think I know how to do that.  If anyone could tlel me how and explain it would be helpful.

---

### Post by CrazyDesi on 2005-07-31
Bump

---

