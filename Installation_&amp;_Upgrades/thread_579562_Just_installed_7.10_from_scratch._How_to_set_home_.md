---
title: "Just installed 7.10 from scratch. How to set /home directory? It only says &quot;sda6&quot; now"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by enthusaroo on 2007-10-18
I had 7.04 install previously. 7.04 was my first time installing and using Ubuntu.

I decided to install 7.10 from scratch. It successfully installed, except for one problem. I can't recall how I managed to set my "/home" directory last time when I installed Feisty. I thought that it would determine the /home directory automatically.

During setting up the partitions I set aside an ext3 partition of 30gigs to be my /home directory. However, the problem is now 7.10 is installed, but there isn't any /home directory set. On my desktop it just says "sda6".

Can someone please tell me how I can set sda6 to be the /home directory for Ubuntu?

---

### Post by enthusaroo on 2007-10-18
*bump*

---

### Post by logos34 on 2007-10-18
post the output from the following commands:
[B]
sudo fdisk -l[/B]

**mount**

---

### Post by enthusaroo on 2007-10-18
> **logos34 said:**
> post the output from the following commands:
[B]
sudo fdisk -l[/B]

**mount**

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0defc2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4052    32547658+   7  HPFS/NTFS
/dev/sda2            9152        9729     4641840   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            4053        5072     8193150   83  Linux
/dev/sda4            5073        9151    32764567+   5  Extended
/dev/sda5            5073        5327     2048256   82  Linux swap / Solaris
/dev/sda6            5328        9151    30716248+  83  Linux

Partition table entries are not in disk order
shaun@shaun-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda6 on /media/sda6 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

---

### Post by logos34 on 2007-10-18
you say that you made a separate 30 GB partition with mountpoint of '/home', but something must have gone awry during installation because sda6 is mounting instead at /media/sda6.  

You'll have to use[ this howto]("http://www.psychocats.net/ubuntu/separatehome") to transfer the home directory to a separate /home on sda6

---

### Post by enthusaroo on 2007-10-18
> **logos34 said:**
> you say that you made a separate 30 GB partition with mountpoint of '/home', but something must have gone awry during installation because sda6 is mounting instead at /media/sda6.  

You'll have to use[ this howto]("http://www.psychocats.net/ubuntu/separatehome") to transfer the home directory to a separate /home on sda6

logos34:

That's the thing. During installation, I only recall it asking for me to set a / (root) and swap. I don't recall it ever asking me to set a /home directory. Perhaps I missed a step somewhere. Does that mean that I should try to reinstall?

---

### Post by logos34 on 2007-10-18
yeah, reinstall might be quicker.  Just make sure to specify /home as well as / and /swap mountpoints this time

---

### Post by pbcartwright on 2007-10-18
if you just started, it might not hurt to redo the installation.. or read his HOW-TO. Basically, when you get to the partitioning part, you have to use the drop-down menu where it shows /dev/sda6 and change the mount point to /home .

---

### Post by enthusaroo on 2007-10-18
> **logos34 said:**
> yeah, reinstall might be quicker.  Just make sure to specify /home as well as / and /swap mountpoints this time

logos34:

The problem is that I don't remember seeing an option to specify /home during the installation. As I mentioned, it only instructed me to set a / (root) and swap. I tried going through some of the options during the last installation. How can I set it as /home?

Cheers

---

### Post by pbcartwright on 2007-10-18
in the partition window, where you selected the root partition, you can also CLICK on /dev/sda6, and... I forget exactly how, but maybe there is an EDIT link below it? for each partition shown on the partition page, you can change the mount point. You can mount your windows partition as /windows if youwant, then run ntfs-3g to be able to read/write to it.

---

### Post by logos34 on 2007-10-18
Do the manual partitioning approach and when you get to the 'prepare parttiions' screen select sda6 and click 'edit partition' button
.  [Then change mountpoint to /home.]("http://img264.imageshack.us/my.php?image=feistydual12xc2.png")

---

### Post by pbcartwright on 2007-10-18
I would suggest reading his HOW-TO web page:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

and/or just rerun the install and do not skip the step about partitioning, until you change the entry for /dev/sda6 to /home

---

### Post by enthusaroo on 2007-10-18
Ah! I've got it now!

I'm in the Live CD reinstalling again. I see what you guys are talking about.

THAT'S SO EASY!

OK. Thank you so much for your great advice! :)

---

### Post by Topsiho on 2007-10-18
You are quite right if you don't remember being asked to set a /home partition: you are not.
You have to set it on your own initiative, and it is wise to do so,  so that when doing a new install you can keep your files and settings without losing them. Just mount the /home partition to the same partition and NOT FORMAT this partition during a later install or reinstall.

But still: it is always wise to back up anything you hate to lose....

Topsiho

---

