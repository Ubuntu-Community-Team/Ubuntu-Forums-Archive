---
title: "Ubuntu installed in raid 0 (software) doesn't start"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by polrpk on 2012-06-19
Hi! 
I have installed last ubuntu 64 bit(alternate version) on my pc (p4 3GHz, 1 GB RAM, 3 HD ATA), with / in a raid 0 (3x 80 GB partition), swap in raid 0 (3x 500 MB) and /boot in a single partition in the beginning of the first disk. I have toggle /boot as bootable. 

System was successfully installed, but after reboot it doesn't start. No error message, no grub crash, nothing. I tried to reinstall two times in other ways (without /boot partition, with LVM): without /boot grub doesn't install in / (no surprise with / in software raid 0), with LVM I've got the same problem (don't start after reboot). I tried to install Debian too, but the problem was the same.

Can you help me to install ubuntu in raid 0? I followed [this guide]("http://wiki.ubuntu-it.org/Installazione/SoftwareRaid"), but unsucessfully. 

My english is far from good, so I ask you a little bit of patience.

Thank you very much!

---

### Post by darkod on 2012-06-19
You say without /boot grub doesn't install in / but even with a separate /boot grub doesn't go on any partition. It goes to the MBR of the disk(s).

Did you install grub2 to the MBR at all? Without it, there will be nothing to boot the system. The bootloader needs to be on the MBR.

If you only install it on one disk, that disk has to be the first boot option in BIOS.

Personally I think you better use RAID5 with three disks, instead of RAID0. Why are you doing this, more transfer speed? If any of the disks die, you lose all the data with RAID0.

---

### Post by polrpk on 2012-06-19
During the installation grub was installed on MBR (/dev/sda). It's the default option. I didn't install grub in the other disks.

BIOS is already set to boot hard disks for first.

I know the risks of raid0, but they are not a problem for me. I want to install the system with raid0 to get maximum of performance. When I tried to install Debian and Ubuntu with raid0, I've seen it takes MUCH less time than a normal installation. Installing on raid1 took much more time than normal. 
So, in my pc the difference is outstanding, at least 30%-40% (maybe more) faster with raid0.

I have followed all guides I found, but system still doesn't boot.

I think the problem is in grub. Maybe the right commands in rescue mode can solve the problem.

I forgot to write a particular: I tried to install debian in raid1 (/ in raid1, swap in raid1, no /boot, grub installed in /, physical volume for RAID set as bootable). After reboot grub didn't boot the system and went to rescue mode.

---

### Post by darkod on 2012-06-19
In live mode, install and run boot-repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Don't run the recommended repair, just the option to create boot info results and post the link it gives you.

Lets see the setup you have, and what can be done.

---

### Post by polrpk on 2012-06-19
Many thanks for help. Here is the result of boot repair:
[http://paste.ubuntu.com/1049048/](http://paste.ubuntu.com/1049048/)

---

### Post by darkod on 2012-06-19
It looks like the configuration in /etc/mdadm/mdadm.conf is not correct or missing.
From live mode, try to assemble the array but you have to add the mdadm package first:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should assemble the md devices. It seems your root is md127. Try mounting it and reading the mdadm.conf with:
```
sudo mount /dev/md127 /mnt
cat /mnt/etc/mdadm/mdadm.conf
```

That should display the mdadm.conf. Can you see the md devices defined there?

While you have md127 mounted at /mnt you might as well try to reinstall grub2 to /dev/sda with:
```
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Hope that would help.

---

### Post by polrpk on 2012-06-19
This is my mdadm.conf:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=49c25a58:a651fa1d:b6e4ad1c:c5146f96 name=ubuntu:0
ARRAY /dev/md/1 metadata=1.2 UUID=db5ccdf2:5064f7f6:f95eb47c:4a7d26bb name=ubuntu:1

# This file was auto-generated on Tue, 19 Jun 2012 11:08:01 +0200
# by mkconf $Id$
```
I don't see md127, but only md0 and md1.

I've got an error after grub-install: Unrecognized option `--boot-directory=/mnt/boot'

---

### Post by darkod on 2012-06-19
I'm not raid expert to help with more difficult issues, let me see if I can someone else to help. Hold on a minute.

I see few things that don't match but I wouldn't like to give you wrong advice.

---

### Post by YannBuntu on 2012-06-19
Hi

> **polrpk said:**
> Many thanks for help. Here is the result of boot repair:
[http://paste.ubuntu.com/1049048/](http://paste.ubuntu.com/1049048/)

Your system on md127 is not detected by os-prober.
Boot-Repair seems to activate the RAID successfully.
Please run Boot-Repair, DON'T update it, click "Recommended repair", indicate the new URL that will appear.

---

### Post by polrpk on 2012-06-19
YES!! It works!
Here's the result of boot repair: [http://paste.ubuntu.com/1049222/]("http://paste.ubuntu.com/1049222/")

A billion of thanks!

Now I try to make a dual boot with xp!:guitar:

---

### Post by YannBuntu on 2012-06-19
Great! :)

Now please could you update Boot-Repair, click "Create BootInfo" and tell me the new URL? (that's just for my information, it won't change your boot)

---

