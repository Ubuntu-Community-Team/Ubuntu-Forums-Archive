---
title: "lost cryptsetup mkinitramfs 'hook'"
date: 2017-09-30
forum: Installation &amp; Upgrades
---

### Post by turtles on 2017-09-30
Greetings I run a bare bones ubuntu and today while attempting to get NFS working I ran 
```
  apt-get update
apt-get dist-upgrade

```
and now when rebooted to the new kernel 4.4.0-96 the  initrd.img was not setup to unlock my encrypted root.
Rebooting to my last working kernel 4.4.0-58 and the initrd.img thankfully still works.

Looks like somehow I lost the config file that tells initramfs-tools about my encrypted root?
Since it was automatic before I am not sure what to do.
Looks like there should be a hook for cryptsetup in one of these:
```
  ls /etc/initramfs-tools/hooks/
  ls /usr/share/initramfs/hooks/ 
```?
I unpacked the working initrd and copied the config/modules file and the  conf.d/cryptroot  to /etc/initramfs-tools/
and re ran ```
mkinitramfs -o test.img -v 4.4.0-96-generic
```
now it asks for my key but the initrd (busybox?)  seems to be missing /sbin/cryptsetup.
I dont seem to have any scripts in the ```
ls -lat /etc/initramfs-tools/scripts/*
```

Any advice on fixing my initramfs-tools for cryptsetup?
Here is my config:
```
cat initramfs.conf 
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#
# Note that configuration options from this file can be overridden
# by config files in the /etc/initramfs-tools/conf.d directory.

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add most filesystem and all harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# BUSYBOX: [ y | n | auto ]
#
# Use busybox shell and utilities.  If set to n, klibc utilities will be used.
# If set to auto (or unset), busybox will be used if installed and klibc will
# be used otherwise.
#

BUSYBOX=auto

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# COMPRESS: [ gzip | bzip2 | lzma | lzop | xz ]
#

COMPRESS=gzip

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify a specific network interface, like eth0
# Overridden by optional ip= bootarg
#

DEVICE=

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

```
Perhaps somehow installing nfs hozed the config?
Thanks in advance!


EDIT looks like a bug: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1256730](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1256730)

Creating the file ```
/usr/share/initramfs-tools/conf-hooks.d/forcecryptsetup
```
with export ```
CRYPTSETUP=y
``` got it working

---

