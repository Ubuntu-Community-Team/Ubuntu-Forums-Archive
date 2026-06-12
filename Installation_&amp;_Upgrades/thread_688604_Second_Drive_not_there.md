---
title: "Second Drive not there?"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by joshdudeha on 2008-02-05
This isn't a major problem for me.
But, after reformatting both my drives.
I added a partition for root system /
Also I added swap partition
and one for my home folder
That was on one of my drives.
On the other one, i made one big partition, /drive 2
but it wont show up in my computer.
How do i recover this?
I'm using Gutsy 
Thanksx

---

### Post by wolfen69 on 2008-02-05
what was drive2 formatted as?

---

### Post by joshdudeha on 2008-02-06
it was formatted as ext3 like the other partitions

---

### Post by joshdudeha on 2008-02-07
Can anyone help?

---

### Post by taurus on 2008-02-07
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by joshdudeha on 2008-02-07
This is the out put :/
 ```
joshua@joshua-desktop:~$ sudo fdisk -l
[sudo] password for joshua:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33153314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         747     6000246   83  Linux
/dev/sda2             748         871      996030   82  Linux swap / Solaris
/dev/sda3             872        4865    32081805   83  Linux

Disk /dev/sdb: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97a997a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3322    26683933+  83  Linux
joshua@joshua-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=911cf723-7161-4e38-a3f6-922e82614e66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=6aa51578-962c-44a0-96ce-f04f463baf72 /drive2         ext3    defaults        0       2
# /dev/sda3
UUID=70d67169-3fb0-4c0e-ac2f-9e716535d95b /home           ext3    defaults        0       2
# /dev/sda2
UUID=2106996e-6ada-4a91-a7d5-1f3dea5557a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
joshua@joshua-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.7G  3.1G  2.3G  58% /
varrun                248M   96K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   76K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              26G  173M   24G   1% /drive2
/dev/sda3              31G  666M   28G   3% /home
joshua@joshua-desktop:~$ 

```
hmm
ive used 1% of that too - dont know how :/

---

### Post by taurus on 2008-02-07
I assume when you said it won't show up you mean there is no icon for /dev/sdb1 (/drive2) on your desktop!   You need to mount it to /media like /media/drive2.  Otherwise, you can still list it with

```
ls -la /drive2
```

---

### Post by joshdudeha on 2008-02-07
How can i mount it properly??
Because, im a sorta beginner with linux
thanks x

---

### Post by joshdudeha on 2008-02-07
Can anyone tell me how to mount this drive in ubby??
Thanks

---

### Post by joshdudeha on 2008-02-08
I guess not ..

---

### Post by taurus on 2008-02-08
Why don't you edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and modify the entry for /dev/sdb1 to look like this.

```

UUID=6aa51578-962c-44a0-96ce-f04f463baf72   **[COLOR="Blue"] /media[/COLOR]**/drive2         ext3    defaults        0       2

```
Save it.  Then, create the new mount point for it.

```
sudo mkdir /media/drive2
```
Reboot.

---

### Post by confused57 on 2008-02-08
This guide has worked for me:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Added: taurus beat me to it...you might want to see the guide to change owner & set permissions.

---

