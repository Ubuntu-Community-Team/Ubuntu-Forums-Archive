---
title: "Resizing the boot partition in Ubuntu"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by spoilt-the-programmer on 2011-07-23
My boot partition(ext4) is of around 8 GB...Now I need more space on it. I am thinking of resizing it using Gparted live...Just want to know whether this is the right procedure or it would corrupt my installation of Ubuntu 11.04??

---

### Post by lmarmisa on 2011-07-23
Welcome to the forums. :D

The resize of your boot partition is only one of the possible options.

Please, open a terminal (Applications -> Accessories -> Terminal), type these commands and post the results:

```

sudo fdisk -l
mount
df -h
sudo du -h --max-depth=1 /

```

Best regards,

Luis

---

### Post by spoilt-the-programmer on 2011-07-23
> **lmarmisa said:**
> Welcome to the forums. :D

The resize of your boot partition is only one of the possible options.

Please, open a terminal (Applications -> Accessories -> Terminal), type these commands and post the results:

```

sudo fdisk -l
mount
df -h
sudo du -h --max-depth=1 /

```

Best regards,

Luis
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x21735800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7841    62873600    7  HPFS/NTFS
/dev/sda3            7841       22598   118541312    7  HPFS/NTFS
/dev/sda4           22599       38913   131049313+   f  W95 Ext'd (LBA)
/dev/sda5           25396       38913   108577792    7  HPFS/NTFS
/dev/sda6           22963       24057     8787968   83  Linux
/dev/sda7           22599       22963     2928640   82  Linux swap / Solaris


/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mrafay/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mrafay)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             8.3G  6.5G  1.4G  83% /
none                  1.2G  696K  1.2G   1% /dev
none                  1.2G  416K  1.2G   1% /dev/shm
none                  1.2G   96K  1.2G   1% /var/run
none                  1.2G     0  1.2G   0% /var/lock
df: `/root/.gvfs': Permission denied



148K	./.pulse
224K	./.adobe
16K	./.android
824K	./.gstreamer-0.10
104K	./.kde
4.0K	./.themes
12K	./.mission-control
20K	./.mono
4.0K	./.dnacache
136K	./.macromedia
4.0K	./Podcasts
4.0K	./Templates
64K	./.armagetronad
4.0K	./.nautilus
4.0K	./Music
222M	./My Programs
4.0K	./Audiobooks
4.0K	./.icons
44M	./.config
12K	./.dbus
4.0K	./Ubuntu One
4.0K	./Public
72K	./.gconfd
36K	./.pki
4.0K	./Videos
4.0K	./Pictures
2.2M	./Documents
96K	./.gnome2
12K	./Desktop
164K	./.fretsonfire
2.0G	./Downloads
4.0K	./.gnome2_private
1.1M	./.libreoffice
48K	./.swt
2.7M	./.thumbnails
100K	./.fontconfig
164K	./workspace
du: cannot access `./.gvfs': Permission denied
65M	./.mozilla
68K	./.compiz
192M	./.cache
3.0M	./.gconf
2.0M	./.local
2.5G	
```.

---

### Post by lmarmisa on 2011-07-23
Apparently you have no unallocated space on your hard drive. So you would need to shrink the 108 GB NTFS partition (**/dev/sda5**) before to enlarge your boot partition (**/dev/sda6**). Gparted (System -> Admin -> Gparted) is a good tool for the shrink operation. If Gparted it is not installed, type this command:

```

sudo apt-get install gparted

```If you wish to enlarge the boot partition, use Gparted too. But you will need to boot your system into an Ubuntu Live CD / USB.

Gparted is a reliable tool but resizing operations are risky. So, consider to make a backup of your system before any change on your partitions.

Best regards,

Luis

---

### Post by spoilt-the-programmer on 2011-07-23
> **lmarmisa said:**
> Apparently you have no unallocated space on your hard drive. So you would need to shrink the 108 GB NTFS partition (**/dev/sda5**) before to enlarge your boot partition (**/dev/sda6**). Gparted (System -> Admin -> Gparted) is a good tool for the shrink operation. If Gparted it is not installed, type this command:

```

sudo apt-get install gparted

```If you wish to enlarge the boot partition, use Gparted too. But you will need to boot your system into an Ubuntu Live CD / USB.

Gparted is a reliable tool but resizing operations are risky. So, consider to make a backup of your system before any change on your partitions.

Best regards,

Luis

Well all is done and i am set to go....have created unallocated space and everything..

Now i have burnt a GParted Live CD based on Debian Live...
When I am booting from it, it is asking for username and password...
the site mentions that username is: "user"
and password is: "live"

but they aren't working...i have tried root and toor but they aren't working too...please help...:(

---

### Post by lmarmisa on 2011-07-23
> **spoilt-the-programmer said:**
> Well all is done and i am set to go....have created unallocated space and everything..

Now i have burnt a GParted Live CD based on Debian Live...
When I am booting from it, it is asking for username and password...
the site mentions that username is: "user"
and password is: "live"

but they aren't working...i have tried root and toor but they aren't working too...please help...:(

Hmmm. You do not need any Gparted Live CD. Use a standard Ubuntu Live CD and select the option "Try Ubuntu" at startup.

Then you will be able to use Gparted for resizing your Ubuntu root partition /dev/sda6.

---

### Post by spoilt-the-programmer on 2011-07-23
Well thanks for all the help and contributing your time :)

---

