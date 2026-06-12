---
title: "[SOLVED] Unable to format mounted encrypted partitions"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by cberman on 2008-08-07
Hey All --

I'm following the debuntu guide on how to install 8.04 over LVM with LUKS ([http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks-page-2-encrypting-partitions](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks-page-2-encrypting-partitions)) and immediately after it has me mount the partitions it wants me to format them.

The problem I'm having is trying to format seems impossible -- the system thinks the drives are in-use. Without mounting the encrypted partitions I can format them normally, but then they wouldn't be encrypted.  Here's what I'm doing:

```
root@ubuntu:~# cryptsetup luksOpen /dev/lvmvolume/encryptedroot rootvolume
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.
```
Then:
```
root@ubuntu:~# mkfs.ext3 -FF -j -m 1 /dev/lvmvolume/encryptedroot
mke2fs 1.40.8 (13-Mar-2008)
/dev/lvmvolume/encryptedroot is apparently in use by the system; will not make a filesystem here!
```
Then checking mount I don't see any /dev/sda listed:
```
root@ubuntu:~# mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
root@ubuntu:~# 

```

I'm at a loss as to how to proceed and I must have this entire drive encrypted (it's a company requirement thing). 

Keep in mind this is all with the Live CD. For some reason on my system (Dell Inspiron 9300 w/ ATI x300) the Alternate CD won't boot up, once I choose Install from the first menu it just goes black and never comes back. First of all -- does anyone know what I'm doing wrong as far as formatting etc goes, and second of all -- any one else have trouble booting from the Alternate CD? I've tried a ton of different burns and the CDs all work on other machines. 
\
\
\
Thanks!!!

---

### Post by tamoneya on 2008-08-08
just unmount them and the format them.  It is the only way that makes sense since it is impossible to format a mounted drive.

---

### Post by cberman on 2008-08-08
I'm not seeing that they are mounted. I can lvchange then as inactive but then I can't work with them.

 Anyway, I went ahead with luksformat instead of cryptsetup and that seems to have worked perfectly. The drive is partitioned, formatted and encrypted. Now when I load installer and it gets to the partitioning portion the installer crashes throwing ubiquity errors in syslog. I'm going to try changing frame buffer modes with the Alternate CD to see if that works.

---

### Post by cberman on 2008-08-08
I was able to enter installer on the Alternate CD using the boot flags vga=0x314 (frame buffer 800x600 16bit). Formatted and encrypted and working great.

---

