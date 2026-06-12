---
title: "How to remove accidental 2nd Feisty install in dual boot?"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-06-02
After some difficulties installing Feisty in a dual boot arrangement, I finally got a successful install, but somehow ended up with 2 copies of Feisty.

How do I determine which one is "active" and then how can I safely remove it?

Thanks

---

### Post by Ken_Lewis81 on 2007-06-02
You need to know which of your hard disk partitions are being used.  The command 'mount' in a terminal window (Applications -> Accessories -> Terminal) will show you what you're presently using.

You could take a note of the partitions you're using, and use GParted (which you need to install via the Add/Remove program or Synaptic) to reclaim the disk space.  That'll be tricky and quite easy to mess up, so take care and make sure you make good backups!  The easier alternative would be to note which partition is mapped to '/home' and then reinstall, choosing manual partitioning and deleting everything you know you don't need.

Good luck!
Take care.
Ken.

---

### Post by Buster95 on 2007-06-03
The "mount" command returns the following.

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda2 on /media/hda2 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (r

I'm sort of guessing from this that the Feisty copy that I'm using is on sda6 and XP is on sda1. Then - where are sda2, 3, 4 and 5? There seems to be no other partitions or feisty copies recognised.

I made the assumption that I had extra copies because the boot screen shows additional Ubuntu kernels. The output of sudo fdisk (below) shows that they are there.

dexter@home-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451    7  HPFS/NTFS
/dev/sda2             262         809     4401810   83  Linux
/dev/sda3             810        9729    71649900    5  Extended
/dev/sda5            9649        9729      650601   82  Linux swap / Solaris
/dev/sda6             810        1174     2931799+  83  Linux

Partition table entries are not in disk order.

I'd appreciate further guidance here to avoid "the mother of all stuff-ups"
Cheers

---

### Post by Ken_Lewis81 on 2007-06-25
Thanks for that information.  I guess that the installation you're using is all squidged up in the sda6 partition, right?

The first listing shows that your first Ubuntu installation is mounted as /media/hda2.  What stuff is installed there?  Do you use it?  And can you tell if your GRUB installation is to the /dev/sda6 or to /dev/sda2?  You can do this by reading the the /boot/grub/menu.lst in Text Editor to see if it points to (HD0,1) or (HD0,4) or (HD0,5), and those last two are there because I'm not sure which of these last two is the right one for your second installation.

Take care.
Ken.

---

