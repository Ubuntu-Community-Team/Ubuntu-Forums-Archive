---
title: "How to partition HD with LVM"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by satimis on 2006-07-31
Hi folks,

PC - AMD64, 1G RAM
CD Installer - ubuntu-6.06-alternate-amd64

I have been working around installing Ubuntu-6.06 and could not figure out how to partition HD with LVM

My HD has 40G in capacity.  I want to make /boot 255M on /dev/hda1.  First I installed Ubuntu-6.06-amd64 from "Ubuntu-6.06 amd64 DVD" trying partitioning HD as follows without success;

/dev/hda2
VolGroup00 20G in size
LogVol01 8G /
LogVol02 10G /home
LogVol03 1G swap (approx)

The rest space will be retained as Free Space for VolGroup01 to install another LinuxOS later

There were preset LVs there with asigned capcity such as;
LV /
LV /home
LV /var
etc.
LV swap

I deleted all of them but can't remove them from the table.  They were still there with Free Space indicated.

I posted my problem on the "Beginners" and was advised to run "Ubuntu-6.06-alternate-amd64" for installation.  Therefore I download its ISO image and started again.  But still I can't manage to partition the HD with LVM.  The situation was same as "Ubuntu-6.06 amd64 DVD"  Hereinunder is the running HD partitions;

$ sudo fdisk -l```

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2342    18812083+   5  Extended
/dev/hda5   *           1          31      248944+  83  Linux
/dev/hda6              32        1004     7815591   83  Linux
/dev/hda7            1005        2220     9767488+  83  Linux
/dev/hda8            2221        2342      979933+  82  Linux swap / Solaris
```

$ sudo df -l```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda6              7692876   2020672   5281428  28% /
varrun                  514148        88    514060   1% /var/run
varlock                 514148         4    514144   1% /var/lock
udev                    514148       100    514048   1% /dev
devshm                  514148         0    514148   0% /dev/shm
lrm                     514148     21540    492608   5% /lib/modules/2.6.15-23-a md64-generic/volatile
/dev/hda7              9614116    133756   8991988   2% /home
/dev/hda5               233303      4127    216729   2% /media/hda5
```

I have been googling around for relevant document on Internet and found many of them there.  But could not find one for Ubuntu.  Please help.  TIA

Remark: to my opinion for installing Ubuntu-6.06 amd64 "Ubuntu-6.06 amd64 DVD" and "Ubuntu-6.06-alternate-amd64" are the same.


Furthermore is there any way converting existing partitions to LV.  Tks.

B.R.
satimis

---

### Post by accumulator on 2006-07-31
I installed Dapper the usual way, without LVM (needing a single 2.1GB partition, the smallest size possible).

Then, I booted into single user mode (ubuntu calls this recovery mode). I created some LVM partitions (type 8E). each partition must be 'formatted'/initialised with pvcreate, e.g. pvcreate /dev/hda5

then, create a volume group, passing along the partitions participating in the volume group:

vgcreate vg /dev/hda5 /dev/hda6 ..etc..

'vg' can be any name you want.

After this you can start creating logical volumes (similar to creating partitions), e.g.:

lvcreate -L 3G -n var vg
lvcreate -L 5G -n home vg
lvcreate -L 10G -n usr vg

format the partitions:
mke2fs -j /dev/vg/var
mke2fs -j /dev/vg/home
mke2fs -j /dev/vg/usr

Then mount these partitions on a temporary mountpoint to access them, e.g.:
mount /dev/vg/usr /mnt/usr
.. do this for all volumes

Then copy over the ubuntu trees to the lvm volumes:
cd /usr
cp -Rp . /mnt/usr
cd /var
cp -Rp . /mnt/var
.. etc.. do this for all volumes

(the -p flag means 'preserve attributes', the -R flag means recursive)

Next, update /etc/fstab to mount your LVM volumes at boot, e.g.:
/dev/vg/usr /usr ext3 defaults 0 0
.. do this for all volumes

Then, remove everything from the original locations:
cd /usr
rm -rf .
cd /var
rm -rf . (you might need to unmount /var/lock and /var/run first)
cd /home
rm -rf .

then, reboot, and keep your fingers crossed :)


see also:
[http://www.tldp.org/HOWTO/LVM-HOWTO.html](http://www.tldp.org/HOWTO/LVM-HOWTO.html)

---

### Post by accumulator on 2006-07-31
However, be prepared for some small problems when putting /var on a LVM volume, see my post on this topic : [http://www.ubuntuforums.org/showthread.php?t=224710&highlight=%2Fvar](http://www.ubuntuforums.org/showthread.php?t=224710&highlight=%2Fvar)

---

### Post by accumulator on 2006-07-31
Oh and dont put the root partition (/) on LVM. There's too many implications with that, unless you're very experienced with the boot process!

---

### Post by satimis on 2006-08-02
Hi accumulator,

Tks for your detail advice.

I'm ready to have a go according to your advice.  Before start I make my final preparation clarifying all points.  Hereinafter will be the steps to be performed 

(if I'm wrong pls correct me.  Tks)

Start recovery mode
After login as administrator
# vgcreate vg /dev/hda6 /dev/hda7 /dev/hda8

Here I expect to clarify.

According to,
$ sudo fdisk -l```

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2342    18812083+   5  Extended
/dev/hda5   *           1          31      248944+  83  Linux
/dev/hda6              32        1004     7815591   83  Linux
/dev/hda7            1005        2220     9767488+  83  Linux
/dev/hda8            2221        2342      979933+  82  Linux swap / Solaris
```

and
$ sudo df -h```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             7.4G  2.1G  5.0G  30% /
varrun                471M   92K  471M   1% /var/run
varlock               471M  4.0K  471M   1% /var/lock
udev                  471M  100K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm
lrm                   471M   22M  450M   5% /lib/modules/2.6.15-26-amd64-generic/volatile
/dev/hda7             9.2G  654M  8.1G   8% /home
/dev/hda5             228M  4.1M  212M   2% /media/hda5
```

/dev/hda1 = /boot (it will not be in the vg)
/dev/hda6 = / (root)
/dev/hda7 = /home
/dev/hda8 = swap  (swap will be in the vg as well ???)

/dev/hda5  (what is this partition?  What is /media/hda5 ???)


I only need 3 LV, i.e. /, /home and swap.

# lvcreate -L 8G -n root vg
# lvcreate -L 10G -n home vg
# lvcreate -L 1G -n swap vg

# mke2fs -j /dev/vg/root
# mke2fs -j /dev/vg/home

# mkdir /mnt/root
# mkdir /mnt/home

# mount /dev/vg/root /mnt/root
# mount /dev/vg/home /mnt/home

# cp -Rp / /mnt/root
# cp -Rp /home /mnt/home


edit /etc/fstab

Original:
$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```


changed to;```

# /etc/fstab: static file system information.
#

vg
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/vg/hda6    /               ext3    defaults,errors=remount-ro 0       1
/dev/vg/hda7    /home           ext3    defaults        0       2
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/vg/hda8    none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

# rm -rf /
# rm -rf /home

Reboot PC

B.R.
satimis

---

