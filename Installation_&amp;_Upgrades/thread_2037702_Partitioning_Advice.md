---
title: "Partitioning Advice"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by som1special2 on 2012-08-05
I have looked endlessly online and come up with nothing. I will come back to the place I always receive good answers and advice! I just purchased a new OCZ SSD 120GB drive and will be installing it into a All in One that has 8GB of RAM in LMDE. 
(SSD - [http://www.ocztechnology.com/ocz-vertex-plus-r2-series-sata-ii-2-5-ssd.html](http://www.ocztechnology.com/ocz-vertex-plus-r2-series-sata-ii-2-5-ssd.html))

  *My question is how I can effectively utilize my partitions on this drive as to maximize speed and help minimize writes.* 

 Previously, I have read that utilizing the standard /boot, /root & /home are all that is necessary for an intermediate install, (which is what I use now plus the /tmp). I do not and will not use swap, nor do I have a another HDD that I will use. 

What are the advantages in partitioning extras like: /usr, /tmp, /opt & /srv AND how much space should one effectively allocate to these partitions? Should I flag these partitions in GParted when installing?

_Here is my proposed scheme for the install:_
***120 GB SSD drive Partition scheme:***

- Primary: JFS = /boot 100mb “flagged”
- Extended:
JFS = /root 12gb (should this be bigger to accommodate more programs?)
JFS = /home (remainder in GB after other partitions allocated)
JFS = /tmp 500mb (should this be larger?)

JFS = /usr ?MB/GB?
JFS = /srv ?MB/GB?
JFS = /opt ?MB/GB?

**_*Please be explicit as possible an try to limit your response to facts and figures rather than rants and opinions.*_**

Thanks in advance for the help.

---

### Post by ratcheer on 2012-08-05
There is no real need to make a bunch of separate partitions. I just use /, /home, and a swap partition for all of my installations and I have never had any problems doing it this way. Also, for multiple distro installations, I let them all share the same swap partition.

Make / at least 20 GB, but I always use 50. /home should be as big as you need for all your downloads, pictures, music, etc. swap should be 8 GB or less. My system, with 8 GB RAM, almost never touches the swap.

I have heard that with an SSD, it is a good idea to make a separate /var partition on a separate physical hard drive, because all the log files are continually being written to. This makes perfect sense to me, but I don't have SSD's, so I have no personal experience with it.

Good luck,
Tim

---

### Post by ajgreeny on 2012-08-05
I would suggest you forget about a separate /boot partition which can cause more problems than it solves.  It is only normally used in special cases or for servers, not desktop computers.

The rest, I would agree with ratcheer, though I have personally never used more than 6GB in my root partition, so think that 10-15GB is plenty big enough, unless you have masses of programs and games installed which may take up lots of disk space. So if you have plenty of disk space stick with the 20GB for root.

No swap means you can not suspend the system or hibernate, I believe, but if that does not matter to you you should be fine with 8GB ram.

---

### Post by oldfred on 2012-08-05
One more for fewer partitions. Herman has some reasons here.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Is there some reason for JFS?

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox ssd
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Some really good info on SSD.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

If only Linux you may want to consider gpt partitioning not MBR(msdos).
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

If you have lots of RAM, then you can mount /tmp in RAM.
SSD Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,discard,errors=remount-ro 0       1
noatime,discard,data=writeback,errors=remount-ro
One other thing that saves writing small files to the SSD as long as you are not doing something that needs a lot of tmp space, since tmp is cleared on boot, is an fstab entry:But writing a DVD may need 4GB?
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0

---

### Post by som1special2 on 2012-08-05
Wanted to go with a non-journaling FS and JFS was only choice as BTRFS has given me nothing but problems. I understand that JFS still journals metadata, but it was the lesser of two evils.

---

### Post by Cheesemill on 2012-08-05
I use ext4 on my SSD but with the journaling turned off.
To do this just boot from a Live CD and run the following command on your partitions:
```
tune4fs -O ^has_journal /dev/sdaX
```

Also a +1 from me for just having / and /home partitions.

---

