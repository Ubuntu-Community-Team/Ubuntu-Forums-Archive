---
title: "Minimal Ubuntu Takes Up 22 GB of Space"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by Spiralagnus on 2012-07-28
I just did a minimal install of Ubuntu 12.04 with the XFCE interface on a new computer with a 1.5 TB hard drive.  

```
df -h
```reveals that 22 GB of hard drive space are used up for the primary partition /dev/sda1:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       1.4T   22G  1.3T   2% /
udev            3.8G  8.0K  3.8G   1% /dev
tmpfs           1.6G  348K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G     0  3.8G   0% /run/shm
```although totaling all of the directories in the root folder using 

```
du -h / --max-depth=0
```reveals that the root directory is only taking up about 1.1 GB of space (as the instructions said a minimal installation would):

```
1.1G    /
```I tried resizing the reserved space using 

```
tune2fs -m 1 /dev/sda1
``` to 1%, but it made no difference.  I'm still getting that 22 GB are used.  What's taking up that extra 21 GB of space?  Any thoughts?

Thanks to the community in advance for your help.

---

### Post by Megaptera on 2012-07-29
Did you set the size of the partitions manually or did you just go with the defaults? I'm wondering if you chose defaults a % of total available  disc is automatically allocated? I'm sure someone will know for sure ...

---

### Post by Elfy on 2012-07-29
Try using

```
sudo du -h --max-depth=1 /
```

---

### Post by Spiralagnus on 2012-07-29
> **Megaptera said:**
> Did you set the size of the partitions  manually or did you just go with the defaults? I'm wondering if you  chose defaults a % of total available  disc is automatically allocated?  I'm sure someone will know for sure ...

The hard drive is a single partition containing the Ubuntu install.  I just chose that option and went with the defaults.

> **Elfy said:**
> Try using

```
sudo du -h --max-depth=1 /
```

Done.  Here's the output.  As you can see, the total size of the folders doesn't add up to anywhere near 22 GB.  (I've installed a bunch of software since my last post, so the total size is a bit larger than the 1.1 GB I quoted earlier but still much less than 22 GB.)

```

548M    /var
0       /proc
8.7M    /bin
4.0K    /mnt
4.0K    /opt
1.3G    /usr
16K     /lost+found
0       /sys
4.0K    /lib64
28K     /tmp
206M    /lib
4.0K    /dev
6.1M    /etc
4.0K    /srv
340K    /run
12K     /media
167M    /home
6.8M    /sbin
4.0K    /root
4.0K    /selinux
25M     /boot
2.3G    /

```

---

### Post by Spiralagnus on 2012-08-12
I was just looking at fdisk and noticed this:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2914025471  1457011712   83  Linux
/dev/sda2      2914027518  2930276351     8124417    5  Extended
/dev/sda5      2914027520  2930276351     8124416   82  Linux swap / Solaris
```

Is it possible that Ubuntu is reserving this much space for swap?  If so, why would an OS like Ubuntu need that much swap space, and is there a way to change it?

---

### Post by sffvba[e0rt on 2012-08-12
> **Spiralagnus said:**
> I was just looking at fdisk and noticed this:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2914025471  1457011712   83  Linux
/dev/sda2      2914027518  2930276351     8124417    5  Extended
/dev/sda5      2914027520  2930276351     8124416   82  Linux swap / Solaris
```

Is it possible that Ubuntu is reserving this much space for swap?  If so, why would an OS like Ubuntu need that much swap space, and is there a way to change it?

Note that your output is in "Blocks" and not in a human friendly measurement.  Not sure the command you are using but there will be a switch to make the output appear in KB/MB/GB ... Best check the man page for the command to see all the switched.


404

---

### Post by Spiralagnus on 2012-08-12
> **not found said:**
> Note that your output is in "Blocks" and not in a human friendly measurement.  Not sure the command you are using but there will be a switch to make the output appear in KB/MB/GB ... Best check the man page for the command to see all the switched.


fdisk doesn't appear to have a human-readable option, but it doesn't matter.  Upon closer inspection, I realize the swap space is a separate partition from the primary one, and it's the primary one that's unusually big.  Any other thoughts as to why the partition reads as 22 GB full?

---

