---
title: "Disk partition full"
date: 2018-03-21
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2018-03-21
Hi,
Before to do a clean install of 16.04LTS I created partition on my disk following advice somewhere that it is a good thing to do.
Last time I tried to upload a batch of photos from my camera it told me not enough space so I ran df which returned 
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev              746876        0    746876   0% /dev
tmpfs             154184     6948    147236   5% /run
/dev/sda4       52763588  6764908  43295324  14% /
tmpfs             770908      500    770408   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs             770908        0    770908   0% /sys/fs/cgroup
/dev/sda3       28705788 26853332    371240  99% /home
/dev/sda1       70423984   397756  66425844   1% /boot
tmpfs             154184       52    154132   1% /run/user/1000


```
telling me that my home disk partition is full.
So my question is how do I save stuff in the other part of the disk?

---

### Post by oldfred on 2018-03-21
It looks like you have a very large / (root) and very small /home?
And most desktops do not need a separate /boot. If LVM or full disk encryption it often has a separate /boot.

I use 25GB for / but have all my data in a large data partition. But I have multiple installs for testing or next version and want same data, but not necessarily same configurations, so do not have separate /home.

Because I only use 25GB for / I have many 25 GB partitions. I have 16.04 as main working install, but just reused my old 14.04 working install as a new 18.04. But will probably reinstall 18.04 once released. Just testing it now. And I have a couple of other installs to experment with settings as I do not want to corrupt my main working install.

I do back up all of /home regularly, some settings, and list of installed apps, so I can restore working install if necessary. I separately backup my data partition.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834) 

Some of the versions have now changed. Note that drive is not fully allocated, or room for more 25GB / partitions or data.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by yancek on 2018-03-21
You have a strange partition setup.  Generally, if there is a separate /home (or for some users, data) partition, it will be by far the largest partition as it should be.  Your df output shows a boot partition which is 2 1/2 times the size of the /home partition.  As pointed out above, a separate boot partition generally isn't needed unless you are using LVM and I rarely see a boot partition larger than 500MB.  

What you could do is create a directory for your photos on the / (root filesystem) partition as there is a lot of space there.  YOu would need to do this as root (using sudo) and then give your general user(s) read/write permissions to that directory or directories.

---

### Post by Jorhel on 2018-03-26
Thanks for all the links, I'll need a long sit down and think to make sense of it all or more than likely of some of it... The strange setting come from not being sure how much was needed where when I created the partition. Is there a way to just resize the partitions without breaking everything? I used gparted to do it under xubuntu 14.04 before to install 16.04. tried to install them side by side but never worked.

---

### Post by oldfred on 2018-03-26
You have to use live installer as partitions you edit cannot be mounted. You still often have to swap-off or unmount swap as live installer will use it if found.

But it depends on where partitions are and how much data.
If expanding right into unallocated space, it can be quick.
Do not queue steps but run each one.
If lots of data it can be a very slow process to move that data, never interrupt it or you lose all data.
Be sure to have good backups.

Post this:
       sudo parted /dev/sda unit s print

---

### Post by Jorhel on 2018-04-09
Thanks
```
Model: ATA ST3160021A (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       143362047s  143360000s  primary   ext4            boot
 3      143362048s  201955327s  58593280s   primary   ext4
 4      201955328s  309436415s  107481088s  primary   ext4
 2      309438462s  312580095s  3141634s    extended
 5      309438464s  312580095s  3141632s    logical   linux-swap(v1)

```

---

