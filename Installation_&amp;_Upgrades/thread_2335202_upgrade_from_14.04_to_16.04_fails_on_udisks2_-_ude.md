---
title: "upgrade from 14.04 to 16.04 fails on udisks2 - udevadm trigger is not permitted"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by chomezski on 2016-08-26
Hi All

Hoping to get some help.

I've performed an upgrade from 14.04 to 16.04 and the upgrade fails on trying to install udisks2, when I try to reboot it boots into the initramfs shell.

I'm now booting from the liveCD and following [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) I'm mounted my root partition and chroot'd to it.

```
kubuntu@kubuntu:~$ sudo mount /dev/sdc1 /mnt/
kubuntu@kubuntu:~$ sudo mount --bind /dev /mnt/dev/
kubuntu@kubuntu:~$ sudo mount --bind /proc /mnt/proc/
kubuntu@kubuntu:~$ sudo mount --bind /sys /mnt/sys/
kubuntu@kubuntu:~$ sudo chroot /mnt/

```

 I run apt-get install -f I get the following:

```
root@kubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
Setting up udisks2 (2.1.7-1ubuntu1) ...
udevadm trigger is not permitted while udev is unconfigured.
dpkg: error processing package udisks2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 udisks2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Following this thread: [https://ubuntuforums.org/showthread.php?t=1567147](https://ubuntuforums.org/showthread.php?t=1567147)

I've tried: 

sudo update-initramfs -u -k all

This doesn't help. I've also ended up trying to remove udisks2 and reinstall but doesnt work. I've tried reinstalling udev but get the following:

```
root@kubuntu:/# apt-get install --reinstall udev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/992 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
(Reading database ... 337886 files and directories currently installed.)
Preparing to unpack .../udev_229-4ubuntu7_amd64.deb ...
Unpacking udev (229-4ubuntu7) over (229-4ubuntu7) ...
Processing triggers for systemd (229-4ubuntu7) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up udev (229-4ubuntu7) ...
addgroup: The group `input' already exists as a system group. Exiting.
A chroot environment has been detected, udev not started.
update-initramfs: deferring update (trigger activated)
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
Setting up udisks2 (2.1.7-1ubuntu1) ...
udevadm trigger is not permitted while udev is unconfigured.
dpkg: error processing package udisks2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
Errors were encountered while processing:
 udisks2                                                                                                                                                                                                                                                                       
E: Sub-process /usr/bin/dpkg returned an error code (1)  

```

Any ideas of where I can go next?

---

### Post by RobGoss on 2016-08-27
Hello and welcome to the forum, I have seen dozens of post like this with users having problems upgrading from **14.04** to **16.04, **this may be caused by skipping distributions and not having the correct updates to make the transition work smoothly this is not the correct way to upgrade from one distribution to another, in my option we should always have the currently version of Ubuntu to keep things stable and upgrade accordingly 

I suggest backing up any important **data** and **files,** do a clean installation of **16.04 **this way you will avoid these situation

---

