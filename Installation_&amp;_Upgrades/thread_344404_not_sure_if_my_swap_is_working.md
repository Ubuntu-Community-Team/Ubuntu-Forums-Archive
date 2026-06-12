---
title: "not sure if my swap is working"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by Mateo on 2007-01-22
Been using ubuntu (with this current install) for about a month and a half.  Every time I start my computer, the swap is turned off.  If I go to gparted, I can see this clearly.   I can right click and press "swapon" and I guess it turns on (although, how do I know if the swap is even working then?).  

so how do I turn the swap on by default?

---

### Post by taurus on 2007-01-22
What does your /etc/fstab look like?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by Mateo on 2007-01-22
```
matthew@matthew-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=faae223e-5c5b-4388-b3d6-bab6f9701640 / ext2 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=3234-38EB /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=8C98CE4098CE2912 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
matthew@matthew-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         937     7083688+   b  W95 FAT32
/dev/sda2   *         938       25461   185401440    7  HPFS/NTFS
/dev/sda3           25530       32301    51196320   83  Linux
/dev/sda4           25462       25529      514080   82  Linux swap / Solaris

Partition table entries are not in disk order
matthew@matthew-desktop:~$ 


```

---

### Post by taurus on 2007-01-22
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   none   swap   sw   0   0
```
Reboot and see if your swap is mounted.

```
free
```

---

### Post by Mateo on 2007-01-22
My swap is on, but if I go to System Monitor > Resources, it says "Used swap 0bytes", is this normal?

---

### Post by Mateo on 2007-01-22
ok, i'll give that a go, then report back.

---

### Post by Mateo on 2007-01-22
Ok, it shows my swap as on in gparted.  here is the output of 'free'

```
matthew@matthew-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035656     453356     582300          0       6732     260396
-/+ buffers/cache:     186228     849428
Swap:       514072          0     514072


```

is that normal for the swap to have 0 as used?  when does it get used?

---

### Post by taurus on 2007-01-22
Yes, it is normal that your swap is not used at all.  Since you have 1GB of RAM, your swap space will probably not be used or will be used very little.  In fact, that's what you want since RAM is much much much faster than swap.

---

### Post by esaym on 2007-01-22
Swap isn't always used

[http://community.smoothwall.org/forum/viewtopic.php?t=21844](http://community.smoothwall.org/forum/viewtopic.php?t=21844)

---

### Post by Mateo on 2007-01-22
So, the only time my swap is used is when my memory exceeds 1gig?  well gosh, that's never going to happen.. unless I have like a movie loaded on 3 workspaces and a game on the 4th!

---

### Post by RChickenMan on 2007-01-23
Or if you decide to explore the wonderful world of virtualization.

---

### Post by esaym on 2007-01-24
> **Mateo said:**
> So, the only time my swap is used is when my memory exceeds 1gig?  well gosh, that's never going to happen.. unless I have like a movie loaded on 3 workspaces and a game on the 4th!

One thing to note is that when you first start ubuntu your ram will quickly fill up.  This is not because apps are using all the memory but because the kernel caches all disk IO's.  when the memory is needed for an app then the memory used by the disk io's is dumped for the needed amount

---

