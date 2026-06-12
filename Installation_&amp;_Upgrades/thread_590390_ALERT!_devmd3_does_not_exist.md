---
title: "ALERT! /dev/md3 does not exist"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Schr on 2007-10-24
Hi,

I upgraded from feisty to gutsy via Upgrade Manager which told me a new release was available.

After all packages were installed and I rebooted the system it stops when trying to mount my / file system

Starting up ...
Loading, please wait
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/md3 does not exists. Dropping to a shell!

Now if I do this on the shell:

modprobe raid1
mdadm --assemble /dev/md0 /dev/mapper/sda1 /dev/mapper/sdb1
mdadm --assemble /dev/md1 /dev/mapper/sda2 /dev/mapper/sdb2
mdadm --assemble /dev/md2 /dev/mapper/sda3 /dev/mapper/sdb3
mdadm --assemble /dev/md3 /dev/mapper/sda4 /dev/mapper/sdb4

It boots. Which is nice. But what should I change that I don't have to type all that?

S

---

### Post by bruban on 2007-10-25
Your raid arrays should be automatically set up at boot.

To confirm that the mdadm package is installed, run the following from a terminal as root.

> aptitude install mdadm 


This package should add the appropriate init.d files.

Are your array definitions correctly defined in /etc/fstab?

Bruce

---

### Post by Schr on 2007-10-25
mdadm is already the newest version.

I'm not sure what array definitions I should have in fstab, but my / partition is defined like this:

```

/dev/md3       /               ext3    defaults,errors=remount-ro 0       1

```

My array definitions /etc/mdadm/mdadm.conf are as follows:

```

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=0ac68973:8304e6a1:30fc3597:b4eef05b
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=7c6bf21c:af844782:591d3ff6:7a4c0f37
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=a1393d51:79f3794d:ade289bc:0d690213
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=d7e81528:9d2c4af5:f92f28e1:854dc282

```

And thosse are the same that I get if I run

```
mdadm --detail --scan
```

S

---

### Post by bruban on 2007-10-25
I assume that you see your raid devices when you type:

```
cat /proc/mdstat
```


What do you get when you type the following:

```
ps -ef | grep mdadm
```


On my box I get:

pc# ps -ef | grep mdadm
root 5854 1 0 20:25 ? 00:00:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog

---

### Post by Schr on 2007-10-31
Hi,

I don't think mdadm --monitor should be running at that point (initramfs shell). After manually assembling the arrays and booting into ubuntu proper I do hava mdadm running.

These raid arrays were originally created when I was using Gentoo and they worked with Dapper and Feisty.

I took the silent option away from my grub and I can see some output more. Nothing in here however helps me further.

[http://img383.imageshack.us/img383/833/311020072jy1.jpg](http://img383.imageshack.us/img383/833/311020072jy1.jpg)

For some reason the raid arrays are not automatically detected (partition type is fd (Linux raid autodetect)).

S

---

