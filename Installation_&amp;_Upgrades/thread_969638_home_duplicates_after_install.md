---
title: "/home duplicates after install"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Ole Juul on 2008-11-03
I just did an install of Kubuntu 8.04 and decided to add a /home partition. The process went smoothly but I don't understand the resulting directories.

The /home/name and numerous OS chosen subdirs (Desk' etc.) were there as expected on the first partition which is sdb6. However, these dirs are duplicated on sdb7.

Can someone explain this mess?
Should I delete the /home/name dirs on sdb6?

---

### Post by taurus on 2008-11-03
Actually, your $HOME directory (as a default) should be in /home/your_login_name so if you want to delete anything, /home is the one you want to delete, not the /home/your_login_name.

What is the layout of your harddrive anyway?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Ole Juul on 2008-11-03
Thankyou for answering taurus. Just for the sake of perspective here, I am installing this on someone else's machine which runs MS-XP on the first disk (soon to be ignored?) and now has a second disk for Linux only.

sudo fdisk -l
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77540508

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005390e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1       60801   488384001    5  Extended
/dev/sdb5           60057       60801     5984181   82  Linux swap /
Solaris
/dev/sdb6               1       30394   244139710+  83  Linux
/dev/sdb7           30395       60056   238259983+  83  Linux

Partition table entries are not in disk order

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=6fb9f59a-2d8f-4854-9f04-b886204c9e75 /               ext3
relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=e19a0453-ab7a-44f8-b58f-c9ece5719bf4 /home           ext3
relatime        0       2
# /dev/sdb5
UUID=015476c7-2247-4876-afa7-0dc88a9ba910 none            swap    sw

0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0
0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0
0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0
0

```
df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             231G  2.7G  217G   2% /
varrun                998M  168K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   60K  998M   1% /dev
devshm                998M     0  998M   0% /dev/shm
/dev/sdb7             226G  3.9G  211G   2% /home
tmpfs                 998M   39M  959M   4%
/lib/modules/2.6.24-21-generic/volatile
tmpfs                 998M   39M  959M   4%
/lib/modules/2.6.24-19-generic/volatile
/dev/sda1             190G   63G  128G  34% /media/disk

```

---

### Post by Ole Juul on 2008-11-03
"... /home is the one you want to delete, not the /home/your_login_name."

I understand. Sorry about my lack of clarity.

It seems that if I write or delete a file in one partition, it changes in the other as well which is very confusing.

---

### Post by taurus on 2008-11-03
> **Ole Juul said:**
> 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             231G  2.7G  217G   2% /
varrun                998M  168K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   60K  998M   1% /dev
devshm                998M     0  998M   0% /dev/shm
/dev/sdb7             226G  3.9G  211G   2% /home
tmpfs                 998M   39M  959M   4%
/lib/modules/2.6.24-21-generic/volatile
tmpfs                 998M   39M  959M   4%
/lib/modules/2.6.24-19-generic/volatile
/dev/sda1             190G   63G  128G  34% /media/disk

```

From the output, everything looks fine to me.  So, you do not need to remove anything because if you remove /home, you can't log in anymore because you would have wiped out your $HOME directory which resides under /home.

Therefore, just enjoy your new Ubuntu then.

---

### Post by Ole Juul on 2008-11-03
Thanks taurus. I'm still a little confused about having two of everything and concerned that I'll be wasting space by filling two partitions with data. Which /home directory tree should I use? The one on sdb6 or the one one sdb7?

---

### Post by taurus on 2008-11-03
/dev/sdb6 is your root while /dev/sdb7 is where /home is.  With Linux/Unix, you need at least a / directory because that is the top level of filesystem.  Then, you can have a separate /home, /usr, /tmp, /var, etc. under /.  In your case, you have three partitions: one for /, one for /home, and one for swap.  Whatever you save to your $HOME directory, it will take up the space from /dev/sdb7, not /dev/sdb6 so you are not doubling the space for the same file.

---

### Post by Ole Juul on 2008-11-03
That's how I'd hoped it would be. :) I'll just continue to use this installation as is and not worry about it then.

Perhaps I'm just seeing some kind of oddity with Konqueror which definately shows two of each file.

Konquorer screen 1:
  /media/sdb6/home/name/samefile.test
Konquorer screen 2:
  /media/sdb7/home/name/samefile.test

Both screens can be shown side by side. Presumably if dragging a file from say sda1 to either of the screens above it would not matter which partition the file is put into as long as it is going to /home.

sigh .... I've got much to learn (vbg)

---

