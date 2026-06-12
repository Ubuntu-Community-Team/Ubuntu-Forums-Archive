---
title: "mdadm RAID Questions"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by cpressland on 2011-02-17
Hi All, I'm currently setting up a new server thats going to essentially run as a FileServer and Transmission-Daemon. I just wanted to run by my plan with you all and see if you guys can foresee any issues and also explain to me what to do in the event of a hard drive failure.

Plan is as follows:

Install 8GB HP USB Memory Stick inside Server in Internal USB Port.
Image Ubuntu 10.04.2 NetBook ISO onto another USB Stick.
Boot NetBoot USB Stick
Install onto Internal USB Stick
Remove NetBoot USB Stick
Boot Ubuntu from Internal USB Stick
Install required packages (samba, ssh, lamp, mdadm, etc)
Install 4 x 2TB HDDs.

Ubuntu installation will be on /dev/sda1 with a 500MB swap partition on /dev/sda2.
RAID Drives will be /dev/sdb /dev/sdc /dev/sdd /dev/sde (total 4 drives)

By my understanding all drives need to be partitioned before mdadm is run on them, for this I will run:

```
Fdisk /dev/sdb
```

Use option N and create a partition the full size of the disk, change it’s type via option T to FD (RAID) and repeat this process on all other disks assigned to RAID.

Once this is completed I’ll reboot the server.

Once back online I run the following command:

```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

This fixes issues with mdadm on Ubuntu from what I read, then I run the following command:

```
madam --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

This should create a RAID volume @ /dev/md0/

Now I need to monitor the syncing via,

```
watch cat /proc/mdstat
```

Once that is complete I need to make a filesystem ontop of this new device, ext4 is going to be the filesystem of choice

```
mkfs -t ext4 /dev/md0
```

and now I need to give it a mount point

```
mount /dev/md0 /home/raid
```

Now, if this all works, my question is this.
What will happen if I pull /dev/sdc out of the server for example?

---

