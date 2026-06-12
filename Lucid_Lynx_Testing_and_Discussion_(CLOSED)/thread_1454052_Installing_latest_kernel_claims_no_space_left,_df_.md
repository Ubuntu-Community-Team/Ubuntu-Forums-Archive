---
title: "Installing latest kernel claims no space left, df claims otherwise?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SleepWalkerX on 2010-04-14
I've been having problems installing the latest kernel with the newest batch of updates.  I'm running 64bit Lucid and everything is updated except for the latest kernel and kernel headers.

```

Installing linux-image-generic and linux-headers-generic:

sudo aptitude install linux-image-generic linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-20{a} linux-headers-2.6.32-20-generic{a} 
  linux-headers-generic linux-image-2.6.32-20-generic linux-image-generic 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.5MB of archives. After unpacking 211MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-image-2.6.32-20-generic 2.6.32-20.30 [30.9MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-headers-2.6.32-20 2.6.32-20.30 [9,864kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-headers-2.6.32-20-generic 2.6.32-20.30 [744kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-headers-generic 2.6.32.20.21 [3,898B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-image-generic 2.6.32.20.21 [3,910B]
Fetched 41.5MB in 31s (1,330kB/s)                                               
Selecting previously deselected package linux-image-2.6.32-20-generic.
(Reading database ... 177946 files and directories currently installed.)
Unpacking linux-image-2.6.32-20-generic (from .../linux-image-2.6.32-20-generic_2.6.32-20.30_amd64.deb) ...
Done.
Unpacking linux-headers-2.6.32-20 (from .../linux-headers-2.6.32-20_2.6.32-20.30_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-20-generic.
Unpacking linux-headers-2.6.32-20-generic (from .../linux-headers-2.6.32-20-generic_2.6.32-20.30_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-20-generic_2.6.32-20.30_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.32-20-generic/include/config/snd/aw2.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-20-generic/include/config/snd/aw2.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_2.6.32.20.21_amd64.deb) ...
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.32.20.21_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.32-20-generic_2.6.32-20.30_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-20-generic (2.6.32-20.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-20-generic
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//conf/initramfs.conf': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//conf/conf.d/resume': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/etc/modprobe.d/i915-kms.conf': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/etc/modprobe.d/libpisock9.conf': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/etc/modprobe.d/radeon-kms.conf': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/blkid': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libblkid.so.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libuuid.so.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/mount.fuse': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/pkill': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//bin/ntfs-3g': No space left on device
mkdir: cannot create directory `/tmp/mkinitramfs_vzAfuA/etc/default': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//bin/setfont': No space left on device
mkdir: cannot create directory `/tmp/mkinitramfs_vzAfuA/var': No space left on device
mkdir: cannot create directory `/tmp/mkinitramfs_vzAfuA/etc/lvm': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/etc/lvm/': Is a directory
mkdir: cannot create directory `/tmp/mkinitramfs_vzAfuA/lib/udev': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/lib/udev/rules.d/': No such file or directory
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/lib/udev/rules.d/': No such file or directory
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/lib/udev/rules.d/': No such file or directory
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/dmsetup': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdevmapper.so.1.02.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdl.so.2': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libselinux.so.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/lvm': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdevmapper-event.so.1.02.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libpthread.so.0': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdevmapper.so.1.02.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdl.so.2': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libreadline.so.6': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libselinux.so.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libncurses.so.5': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA/sbin/vgchange': No space left on device
mkdir: cannot create directory `/tmp/mkinitramfs_vzAfuA/lib/udev': No space left on device
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/lib/udev/rules.d/': No such file or directory
cp: cannot create regular file `/tmp/mkinitramfs_vzAfuA/lib/udev/rules.d/': No such file or directory
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//sbin/dmsetup': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdevmapper.so.1.02.1': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libdl.so.2': No space left on device
ln: creating symbolic link `/tmp/mkinitramfs_vzAfuA//lib/libselinux.so.1': No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-premount/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/local-bottom/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/init-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/nfs-top/ORDER: No space left on device
/usr/sbin/mkinitramfs: 329: cannot create /tmp/mkinitramfs_vzAfuA/scripts/nfs-top/ORDER: No space left on device
FATAL: Could not open /tmp/mkinitramfs_vzAfuA/lib/modules/2.6.32-20-generic/modules.dep.temp for writing: No space left on device
rm: cannot remove `/tmp/mkinitramfs_vzAfuA/lib/modules/2.6.32-20-generic/modules.*map': No such file or directory
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.32-16-generic
Found initrd image: /boot/initrd.img-2.6.32-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic

```

Setting up linux-image-generic (2.6.32.20.21) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-20-generic; however:
  Package linux-headers-2.6.32-20-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-20 (2.6.32-20.30) ...
Errors were encountered while processing:
 linux-headers-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 1 broken [+1].

Its claiming no space is left on the device so I decided to check with df -h.

Output of df -h:
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G  4.8G  8.7G  36% /
none                  495M  364K  495M   1% /dev
none                  500M   12M  488M   3% /dev/shm
none                  500M  376K  499M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
/dev/sda5             261G  144G  104G  59% /home

Does this look right?  When I first installed (from Beta 1) I only installed to a root partition (/dev/sda1) and home partition (/dev/sda5).  Not sure why the /dev, /var/run, /lib/init/rw directories are showing only 500 megabytes..  

I am running ext4 and I ran fsck during boot to check the filesystem (as well as testing it from the beta 1 livecd) and it seemed fine.  AFAIR, it didn't report any errors.

Any ideas?

edit:  The problem was when Ubuntu formatted my root partition it didn't create enough inodes.  You can check by typing df -i.  If it shows 99%, its a problem.  The solution is to reformat (luckily, you created a separate partition for /home, riiight?).  Manually format the disk with a livecd and the command "mkfs.ext4 -T news /dev/sdXX" before you run the installer.  It'll reformat your disk.  Specifying -T news optimizes the ratio of inode files to cater to lots of smaller files. I think it has a performance impact, but it lets you have more files..

---

### Post by SleepWalkerX on 2010-04-15
Perhaps its just a bug in ext4..  I guess if I still get this problem I'll just reinstall over my / partition with the final of lucid.

---

### Post by james_xxx on 2010-04-20
I am running into either the same or a similar problem trying to install linux-headers-2.6.32-20-generic after updating today.

This is on a Dell Mini 9 with an 8GB SSD, so disk space is tight, but Nautilus and 'df' both show there still being ca. 450MB of free space in /.

I'd love to learn how to get by this.

---

### Post by james_xxx on 2010-04-21
Bump.

Are there no others running into this issue?

---

### Post by james_xxx on 2010-04-21
OK, I was able to rectify this by removing most older kernels on this system.

Once this finished, I was left with 1.3GB free space in the root fs, which apparently gave the kernel headers room enough to unpack and install.

---

