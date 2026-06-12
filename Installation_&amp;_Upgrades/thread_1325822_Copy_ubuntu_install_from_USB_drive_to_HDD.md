---
title: "Copy ubuntu install from USB drive to HDD"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by dolphy on 2009-11-13
I won a netbook today at an IBM conference and immediately removed that malware legacy OS called windows.  I have Ubuntu installed on a USB thumb drive and I would like to copy it to the netbook's HDD.  Any help on how this is done would be great.

Thanks!

---

### Post by lemming465 on 2009-11-15
In general it is easier to run a [fresh install from USB media]("https://help.ubuntu.com/community/Installation/FromUSBStick") than to clone and adapt a running install between disk devices.  For the clone procedure you'd need to reformat the hard drive, copy the files, and fix the boot process.  E.g. 
1. use a partition manager (fdisk, gparted) to make your preferred disk layout, e.g. sda1 for / and sda2 for swap, or something.
2. format the partitions, e.g. mkfs -t ext3 /dev/sda1; mkswap /dev/sda2
3. copy the files.  Assuming /dev/sda1 is mounted at /media/sda1, something like```

sudo -i
umask 0
mkdir /media/sda1/{dev,media,mnt,proc,sys,selinux}
cd /
tar cf - bin boot etc home lib* root sbin usr var | (cd /media/sda1 && tar -xf -)
cd /media/sda1
for f in dev proc sys; do mount -o bind /$f $f; done
chroot .
nano /etc/fstab  # change root mount to sda1 and swap to sda2
grub-install /dev/sda

```
The grub process is a little different if you used grub2, which would be required if you formatted the filesystem containing /boot with ext4.

---

