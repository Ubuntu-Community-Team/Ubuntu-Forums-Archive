---
title: "[SOLVED] 55Gb unused"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by gleble on 2008-10-16
I have Hardy on my laptop, it takes up about 10Gb When I look at Computer I find ther are 55Gb of unused space that ubuntu cannot access. How can I let ubuntu use this unused space

---

### Post by wannadumpwindows on 2008-10-16
How many threads are you going to start on the same topic?

You need to give people time to find your thread and answer your question. Bumping or starting a new thread in less than 24 hours isn't the best idea. Everyone wants help quickly, but sometimes you just have to be patient.

Other thread:
[http://ubuntuforums.org/showthread.php?t=949404]("http://ubuntuforums.org/showthread.php?t=949404")

---

### Post by gleble on 2008-10-16
Started it here coz it was in the wrong place. Sorry I didn't delete the other one

---

### Post by wannadumpwindows on 2008-10-16
Just keep it in mind for the future. Not a huge deal.

---

### Post by Elfy on 2008-10-16
Can you post the outputs of
```
sudo fdisk -l
cat /etc/fstab
df -h
```

If the 55Gb is there in nautilus what does it say if you try and utilise it?


Can you also report your other thread using the button for a mod to either delete or merge it please.

---

### Post by gleble on 2008-10-16
As root I can access the 55Gb and save things there but hardy does not recognize it i.e programs can't use it, I get told I've run out of memory

```
neil@neil-laptop:~$ sudo fdisk -l
[sudo] password for neil: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6959135

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2858    22956853+  83  Linux
/dev/sda2            2859        9729    55191307+   5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris
/dev/sda6            9427        9545      955836   82  Linux swap / Solaris
/dev/sda7            2859        9240    51263352   83  Linux
/dev/sda8            9241        9426     1494013+  82  Linux swap / Solaris

Partition table entries are not in disk order
neil@neil-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ca2cb20a-7ce6-4097-8924-cf69362e296e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9a9cfa9f-9c98-4636-9a73-410f9806d559 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
neil@neil-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              22G   20G  1.2G  95% /
varrun                248M  136K  247M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   56K  248M   1% /dev
devshm                248M   28K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       22G   20G  1.2G  95% /home/neil/.gvfs
/dev/scd0              62M   62M     0 100% /media/cdrom0
/dev/sda7              49G  2.8G   44G   6% /media/disk
neil@neil-laptop:~$ 
```

---

### Post by Elfy on 2008-10-16
I assume that it is sda7 which you want to be able to access. You can add it to fstab so that it mounts on boot and have permissions for you. You can change /data to anything you wish , but do so in fstab as well

```
sudo mkdir /media/data
sudo cp /etc/fstab /etc/fstab.1610
gksudo gedit /etc/fstab
```

Add this line to end of file

```
/dev/sda7 /media/data  ext3 user 0 2
```

Run commands to give permissions, replace user with your username

```
sudo chown -R user:user /media/data
sudo chmod 770 /media/data
```

Unmount disk from automount and remount to /data

```
sudo umount /media/disk
sudo mount -a
```

Stop at errors and post back here, once you have the partition mounted and available I would be looking to move some of the data you have in your home to it where possible as you are close to full.

In addition you have 3 swap partitions for some reason - one is mounted by fstab, where did the others come from?

---

### Post by gleble on 2008-10-16
Thanks I can put stuff there easily now. What's fstab?
Incidentally how do I delete a post?

---

### Post by Elfy on 2008-10-16
Fstab is a file which > typically lists all available disks and disk partitions, and indicates how they are to be initialized or otherwise integrated into the overall system's file system. 

Can you mark the thread solved please - use thread tools at top of page.

To delete a post or thread you need to report it and ask a mod to do it. In the left panel of each post below under the thanks etc are 2 icons - one is online/offline the other is to report - it used to say 'report' - nice and obvious - but it's been upgraded apparently ;)

---

