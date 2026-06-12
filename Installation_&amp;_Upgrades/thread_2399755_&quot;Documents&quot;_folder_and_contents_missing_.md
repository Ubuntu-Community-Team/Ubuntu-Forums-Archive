---
title: "&quot;Documents&quot; folder and contents missing in ubuntu 18.04"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by vivekcmmacs on 2018-08-29
Hi,
       Today "Documents" folder and contents missing all of sudden. Also computer shows more free space compared to before. Most of my data was in Documents folder only and no back up. Kindly help friends. Also attaching the screenshot for reference

---

### Post by aysiu on 2018-08-30
Did you actually delete the Documents folder? Do you have a separate /home partition?

Can you post back here the output of these commands?

**List the contents of your home directory**
```
ls -al ~/
```

**Disks set to be mounted at boot time**
```
cat /etc/fstab
```

**Partitions and disks**
```
sudo fdisk -l
```

**Mounted partitions and free space on each**
```
df -h
```

---

### Post by vivekcmmacs on 2018-08-30
Documents folder was never deleted and suddenly it went off
Commands are in bold italics and output is posted below...[I][B]
ls -al ~/[/B][/I]
```
total 180
drwxr-xr-x 25 vivek vivek  4096 Aug 30 10:26 .
drwxr-xr-x  3 root  root   4096 Aug 27 17:25 ..
drwxr-xr-x  3 vivek vivek  4096 Aug 28 10:21 .adobe
-rw-rw-r--  1 vivek vivek   119 Aug 28 17:25 .apport-ignore.xml
-rw-------  1 vivek vivek  3396 Aug 30 10:15 .bash_history
-rw-r--r--  1 vivek vivek   220 Aug 27 17:25 .bash_logout
-rw-r--r--  1 vivek vivek  3771 Aug 27 17:25 .bashrc
drwx------ 21 vivek vivek  4096 Aug 29 16:10 .cache
drwx------ 26 vivek vivek  4096 Aug 30 10:00 .config
drwx------  3 root  root   4096 Aug 27 17:37 .dbus
drwxr-xr-x 11 vivek vivek  4096 Aug 30 10:05 Desktop
drwxr-xr-x  9 vivek vivek 20480 Aug 29 16:17 Downloads
-rw-r--r--  1 vivek vivek  8980 Aug 27 17:25 examples.desktop
drwx------  3 vivek vivek  4096 Aug 28 16:59 .gnome
drwx------  3 vivek vivek  4096 Aug 27 17:34 .gnupg
drwx------  4 vivek vivek  4096 Aug 28 12:44 .googleearth
drwxr----- 24 vivek vivek 16384 Aug 29 14:59 hplip-3.18.7
-rw-------  1 vivek vivek  5338 Aug 30 10:00 .ICEauthority
drwx------  3 vivek vivek  4096 Aug 27 17:33 .local
drwx------  5 vivek vivek  4096 Aug 27 17:35 .mozilla
drwxr-xr-x 10 vivek vivek  4096 Aug 30 10:26 Music
-rw-------  1 vivek vivek    64 Aug 27 17:43 .octave_hist
drwxrwxrwx  2 vivek vivek  4096 Aug 27 20:44 PDF
drwxr-xr-x  4 vivek vivek 12288 Aug 29 16:58 Pictures
drwx------  3 vivek vivek  4096 Aug 28 16:59 .pki
-rw-r--r--  1 vivek vivek   807 Aug 27 17:25 .profile
drwxr-xr-x  2 vivek vivek  4096 Aug 27 17:33 Public
drwx------  3 vivek vivek  4096 Aug 28 12:52 .sane
drwxr-xr-x  4 vivek vivek  4096 Aug 28 17:12 snap
drwx------  2 vivek vivek  4096 Aug 28 14:27 .ssh
-rw-r--r--  1 vivek vivek     0 Aug 27 17:37 .sudo_as_admin_successful
drwxr-xr-x  2 vivek vivek  4096 Aug 30 10:24 temp
drwxr-xr-x  2 vivek vivek  4096 Aug 29 15:48 Templates
drwxr-xr-x  3 vivek vivek  4096 Aug 28 11:07 Videos
```


***cat /etc/fstab***
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2459a7ae-9f9e-4583-8b87-97626df8b539 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=59F6-B9A9  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```
***sudo fdisk -l***
```
Disk /dev/loop0: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 87E10802-C2C3-43C8-BFD6-49ADA2295A63

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 976771071 975720448 465.3G Linux filesystem
```


*** df -h***
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           382M  1.8M  381M   1% /run
/dev/sda2       457G  133G  301G  31% /
tmpfs           1.9G   35M  1.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop1       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop2       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop0      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop4      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop5      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop3       87M   87M     0 100% /snap/core/4917
/dev/loop6       15M   15M     0 100% /snap/gnome-logs/37
/dev/sda1       511M  4.7M  507M   1% /boot/efi
tmpfs           382M   16K  382M   1% /run/user/121
tmpfs           382M   40K  382M   1% /run/user/1000
```

---

### Post by vivekcmmacs on 2018-08-31
"bump"

---

### Post by ubfan1 on 2018-08-31
Maybe it got moved into some other directory.  At a terminal (start one with Ctrl + Alt + t or from the launchpad) and type:
```
find ~/ -name Documents
```
If you find it in some other location, like Downloads, move it back to your home.

---

### Post by aysiu on 2018-09-04
Yeah, looks as if you don't have a separate /home partition, so it's probably moved accidentally. Maybe try locating it? It's certainly not in your home folder, even though you have Desktop, Downloads, Pictures, Music, etc. ```
locate Documents
```

---

### Post by vivekcmmacs on 2018-09-05
Dear [**[COLOR=#000000]ubfan1[/COLOR]**]("https://ubuntuforums.org/member.php?u=1256996") & aysiu...thanks for the replies . As i told in my 1st post...All of a sudden, Documents folder is missing and hard disk also showing more free space. locate and find document does not show any result.

---

### Post by sporksrule on 2018-09-05
Friend, the only thing I am finding is this recommendation: [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

You would need to login with a live usb drive and then run extundelete.

---

