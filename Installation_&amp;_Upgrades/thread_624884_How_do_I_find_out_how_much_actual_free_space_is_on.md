---
title: "How do I find out how much actual free space is on my ubuntu partition?"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-11-27
I wan't to reinstall Ubuntu on a new computer and I wan't to see how much space my current installation occupies so I can size the new partition accordingly. But I can't figure out how much space is actually used on my Ubuntu partition. Different programs/utilities report different information.

"Partition Editor": Size: 36 GB, used: 26.3 GB, unused: 9.7 GB
System Monitor: Total (size): 17.7 GB, used: 8.0 GB, free: 9.7 GB
Nautilus*: Space used by all folders: 4.5 GB. free space: 8.8 GB
partimage**: Size: 36 GB, used: 8.3 GB, free space: 9.7 GB

*Mounting sda2 (my Ubuntu installation partition) running Ubuntu on a Live CD, selecting all folders, right-click and "Properties". It says "(some contents unreadable)" in the dialog though.

**partimage is a program I use for backup up partitions, it has worked great so far.

When partimage makes a backup the resulting (non-compressed) image file is 8.3 GB and all the data from the partition should be contained in that file.

Here's the output for **fdisk -l** (it's sda2):

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034c46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           60541       60801     2096482+  82  Linux swap / Solaris
**/dev/sda2           55841       60540    37752750   83  Linux**
/dev/sda3               1        9791    78646176   83  Linux
/dev/sda4            9792       55840   369888592+  83  Linux

```

I'm fairly sure that the correct size of the partition is 36 GB but I can't figure out how much space is actually used. It doesn't add up...

**EDIT:**

Here's the output from *dd* with the partition mounted on the Live CD:

```
ubuntu@ubuntu:~$ sudo du -s -h /media/sda2
7.9G    /media/sda2
```

Disk Usage Analyzer reports the same as System Monitor.


Thanks for your input.

---

### Post by Steve1961 on 2007-11-27
Try the following command:

df -h -T

---

### Post by runesvend on 2007-11-27
OK. Here's the output:

```
ubuntu@ubuntu:~$ df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
tmpfs        tmpfs    506M   16M  491M   3% /lib/modules/2.6.22-14-generic/volatile
tmpfs        tmpfs    506M   16M  491M   3% /lib/modules/2.6.22-14-generic/volatile
varrun       tmpfs    506M   88K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   96K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
tmpfs        tmpfs    506M   16K  506M   1% /tmp
/dev/sda2     ext3     18G  8.0G  8.9G  48% /media/sda2
```

---

### Post by Steve1961 on 2007-11-27
Looks like this line is what you want:

/dev/sda2     ext3     18G  8.0G  8.9G  48% /media/sda2

---

### Post by runesvend on 2007-11-27
But fdisk reports the size to be (60540 - 55841 =) 4699 cylinders of 8225280 bytes which equals 38,650,590,720 bytes which is 36 GB. Is it not telling the truth? GParted and partimage says the same, 36 GB.

---

### Post by Steve1961 on 2007-11-27
There doesn't seem to be a discrepancy on my system between the different programmes so I'm not sure what to suggest.  Anyone have any ideas?

---

### Post by reikoshea on 2007-11-27
du tells you how much you have used.

df tells you how much is free...

im confused about what you are looking for.


EDIT
I now see what youre talking about.  Thats pretty wicked.

My fdisk -l shows no discrepency either.


It sounds like the file system isnt filling the partition, which is more than possible.  I would rely on df rather than FDisk.

Here's how to resize the ext3 system:
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by runesvend on 2007-11-28
Thanks for your input guys. I think you're on to something reikoshea, and I think I know why.

I initially installed Ubuntu on an 18 GB partiton and I moved the data from this partition it to a partition on a new hard drive when I got a faster one. I didn't have much space left on the 18 GB partition on the old drive so on the new drive I made a 36 GB partition for the Ubuntu installation. I then created an image of the old 18 GB partiton with *partimage* and wrote it to the new 36 GB partiton on the faster hard drive.

I think that *partimage* must have, in the image, included some information about the size of the partition, thus, when writing the 18 GB partition image to my new 36 GB partition, it looks like the new partition is only 18 GB in size when in fact 36 GB has been allocated for that partition.

I think I will try resizing the partition with the method you linked to just to see if it works if I, at some other point in time, will need to move a partition to a new hard drive.

**Quick question:** If I wanted to avoid doing this, is there another method for moving all the data of one partition onto another, larger or smaller, partition? I decided not to use *cp* as I suspected it wouldn't handle all the files correctly and make a perfect copy but I don't know if that's true.

---

### Post by reikoshea on 2007-11-28
rsync -a

---

