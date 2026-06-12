---
title: "no boot after upgrading to 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by gnikol on 2009-11-17
Hi,
I upgraded ubuntu from 9.04 to 9.10 on an ACER Aspire 5310 laptop . After finishing upgrade, the computer cold not boot.
The error messages are:

init: sreadahead main process (2143) terminated with status 1
mountall: /proc: unable to mount: Device or resource busy
mountall: /proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't
init: mountall main process (2144) terminated with status 1
General error mounting filesystems
A maintenance shell will now started 
CONTROL-D will terminate this shell and re-try
Give root password for maintenance 
(or type Control-D to continue)


Giving root password I am entering to maintenance mode
The result of the mount command is:
# mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,realtime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


The fstab file is:
#cat /etc/fstab

#/dev/sda1
UUID=471a032b-9cc7-412c-b4f0-47f6e8d3a35c  /  ext3  defaults,errors=remount-ro   0  1
#/dev/sda5
UUID=64e4b8ef-288e-497c-a29d-c2504d5df1c9  none   swap  sw  0  0
/dev/scd0   /media/cdrom0  udf,iso9660  user,noauto  0  0


Any ideas?

Thanks in advance
George

---

### Post by whiskers75 on 2010-03-05
try typing "fsck":KS

---

