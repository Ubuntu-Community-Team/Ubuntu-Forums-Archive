---
title: "blkid and zpool import are hanging forever, Ubuntu 20.04.1 LTS"
date: 2020-09-15
forum: Installation &amp; Upgrades
---

### Post by darxus2 on 2020-09-15
It looks like this started from an automatic upgrade on September 1st:

The parent of this was: /bin/sh /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg

```
Sep01   0:00 /bin/sh /etc/grub.d/10_linux_zfs
Sep01   0:00  \_ /bin/sh /etc/grub.d/10_linux_zfs
Sep01   0:00      \_ zpool import -f -a -o cachefile=none -o readonly=on -N
```
I was trying to install something, I got an error that a file was locked, I tracked it down to this stuff, and killed off what I could.  Now "dpkg --configure -a" always hangs on zpool import, or blkid.  And I have lots of those zpool import and blkid processes unkillable (kill -9 does not succeed).  I have one zpool.  It's mounted and working fine.  I wouldn't mind unmounting it.  I have not tried rebooting, because I have no faith it will succeed.

The blkid hang looks like:
```

/bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-5.4.0-42-generic.new 5.4.0-42-generic
  \_ /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
      \_ /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
          \_ /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
              \_ blkid -l -t UUID=55e42e8c-9316-46bf-b6a3-888f7368c779
```

This machine was upgraded from the previous LTS maybe a few weeks ago.  I did lots of "apt -f install" and re-running "apt update && apt dist-upgrade" afterward to make sure it was clean.  

Okay, it looks like this problem must have started with this unattended upgrade on September 9th.  **Upgrading grub **to version 2.04-1ubuntu26.3**.**  Then I noticed it trying to install something last night, September 14th:
 
```

Start-Date: 2020-09-01  06:00:55
Commandline: /usr/bin/unattended-upgrade
Upgrade: alsa-ucm-conf:amd64 (1.2.2-1ubuntu0.1, 1.2.2-1ubuntu0.2), libasound2-data:amd64 (1.2.2-2.1ubuntu1, 1.2.2-2.1ubuntu2), libasound
2:amd64 (1.2.2-2.1ubuntu1, 1.2.2-2.1ubuntu2)
End-Date: 2020-09-01  06:00:56

Start-Date: 2020-09-01  06:01:03
Commandline: /usr/bin/unattended-upgrade
Install: linux-tools-5.4.0-45-generic:amd64 (5.4.0-45.49, automatic), linux-tools-5.4.0-45:amd64 (5.4.0-45.49, automatic)
Upgrade: linux-tools-virtual:amd64 (5.4.0.42.46, 5.4.0.45.49)
End-Date: 2020-09-01  06:01:05

Start-Date: 2020-09-01  06:01:11
Commandline: /usr/bin/unattended-upgrade
Upgrade: libpulsedsp:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.1-1ubuntu3.6), pulseaudio:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.1-1ubuntu3.6), 
libpulse0:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.1-1ubuntu3.6), libpulse-mainloop-glib0:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.1-1ubuntu3.6)
, pulseaudio-module-bluetooth:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.1-1ubuntu3.6), pulseaudio-utils:amd64 (1:13.99.1-1ubuntu3.5, 1:13.99.
1-1ubuntu3.6)
End-Date: 2020-09-01  06:01:22

Start-Date: 2020-09-01  06:01:28
Commandline: /usr/bin/unattended-upgrade
Upgrade: grub-common:amd64 (2.04-1ubuntu26.2, 2.04-1ubuntu26.3), grub2-common:amd64 (2.04-1ubuntu26.2, 2.04-1ubuntu26.3), grub-pc:amd64 
(2.04-1ubuntu26.2, 2.04-1ubuntu26.3), grub-pc-bin:amd64 (2.04-1ubuntu26.2, 2.04-1ubuntu26.3)

Start-Date: 2020-09-14  21:10:15
Commandline: apt install libgl1-mesa-dri:i386 libgl1:i386

```

---

### Post by darxus2 on 2020-09-15
# strace -o blkid.log blkid -l -t UUID=55e42e8c-9316-46bf-b6a3-888f7368c779

The end of blkid.log (this machine does not have a floppy drive):

```

openat(AT_FDCWD, "/sys/dev/block/11:0", O_RDONLY|O_CLOEXEC) = 4
faccessat(4, "partition", F_OK)         = -1 ENOENT (No such file or directory)
openat(4, "dm/uuid", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
close(4)                                = 0
lstat("/dev", {st_mode=S_IFDIR|0755, st_size=5080, ...}) = 0
lstat("/dev/fd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(0x2, 0), ...}) = 0
stat("/dev/fd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(0x2, 0), ...}) = 0
lstat("/dev", {st_mode=S_IFDIR|0755, st_size=5080, ...}) = 0
lstat("/dev/fd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(0x2, 0), ...}) = 0
access("/dev/fd0", F_OK)                = 0
stat("/dev/fd0", {st_mode=S_IFBLK|0660, st_rdev=makedev(0x2, 0), ...}) = 0
openat(AT_FDCWD, "/sys/dev/block/2:0", O_RDONLY|O_CLOEXEC) = 4
openat(4, "dm/uuid", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
close(4)                                = 0
openat(AT_FDCWD, "/dev/fd0", O_RDONLY|O_CLOEXEC

```

---

### Post by darxus2 on 2020-09-15
(this had an incorrect link)

---

### Post by darxus2 on 2020-09-15
I opened a bug on blkid by running ubuntu-bug on one of its hung instances:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1895686](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1895686)

---

