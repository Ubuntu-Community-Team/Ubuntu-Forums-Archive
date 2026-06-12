---
title: "Can't boot with any kernel in ubuntu 15.04"
date: 2015-05-31
forum: Installation &amp; Upgrades
---

### Post by rimas2 on 2015-05-31
When use one kernel I have acpi errors, others show init errors, other sync errors, and so on. I can chroot into broken partition, but for same reasons it updates just current Lubuntu which one is working, but not the ubuntu 15.04

What I do is:

sudo blkid 
sudo mount /dev/sda1  /mnt
for i in /sys /proc /etc /run /dev /pts; 
do sudo mount --bind "$i" "/mnt$i";
 done
sudo cp /etc/resolv.conf /mnt/etc/
sudo chroot /mnt

I am really stuck after these two days of trying. Please help !

---

### Post by rimas2 on 2015-05-31
This is what I have:
root@rimas-netbook:/# update-initramfs -u -v
dpkg: warning: version 'uname' has bad syntax: version number does not start with a digit
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
Available versions:  uname 3.19.0-16-generic 3.13.0-40-generic 3.13.0-39-generic 3.13.0-35-generic 3.5.0-41-generic uname -r
Keeping /boot/initrd.img-uname.dpkg-bak
update-initramfs: Generating /boot/initrd.img-uname
dpkg: warning: version 'uname' has bad syntax: version number does not start with a digit
grep: /boot/config-uname: No such file or directory
linux-2.6 misses gzip support, using gzip
WARNING: missing /lib/modules/uname
Device driver support needs thus be built-in linux image!
depmod: FATAL: uname: not absolute path.
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/i386-linux-gnu/libudev.so.1
Adding library /lib/i386-linux-gnu/libc.so.6
Adding library /lib/i386-linux-gnu/libpthread.so.0
Adding library /lib/ld-linux.so.2
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/i386-linux-gnu/libblkid.so.1
Adding library /lib/i386-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fuse
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook kmod
Adding binary /bin/kmod
Calling hook mountall
Calling hook thermal
Calling hook udev
Adding binary /lib/systemd/systemd-udevd
Adding library /lib/i386-linux-gnu/libselinux.so.1
Adding library /lib/i386-linux-gnu/libkmod.so.2
Adding library /lib/i386-linux-gnu/libacl.so.1
Adding library /lib/i386-linux-gnu/libpcre.so.3
Adding library /lib/i386-linux-gnu/libdl.so.2
Adding library /lib/i386-linux-gnu/libattr.so.1
Adding binary /bin/udevadm
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/scsi_id
Calling hook zz-busybox
Adding binary /bin/busybox
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/i386-linux-gnu/libntfs-3g.so.853
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook fixrtc
Adding binary /sbin/dumpe2fs
Adding library /lib/i386-linux-gnu/libext2fs.so.2
Adding library /lib/i386-linux-gnu/libcom_err.so.2
Adding library /lib/i386-linux-gnu/libe2p.so.2
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/i386-linux-gnu/libdevmapper.so.1.02.1
depmod: ERROR: could not open directory /tmp/mkinitramfs_3cUmi3/lib/modules/3.13.0-53-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
Building cpio /boot/initrd.img-uname.new initramfs

---

