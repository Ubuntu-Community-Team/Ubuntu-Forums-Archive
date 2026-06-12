---
title: "Installed / and /home on different partitions but ended up with two homes."
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by evilbrent on 2014-05-30
So I've had a go at installing Ubuntu 12.04 with / on a separate partition to /home. My intention was to be able to do completely fresh installs without having to overly risk my family's data. And I've also got a separate ~40GB partition intended for playing around with other linux flavors etc. Currently it has xubuntu 10.04 on it. There's a swap as well, and a separate 2TB HDD.

But my problem is that when I go to click on "Home" in nautilus it takes me to the wrong partition. I was expecting it to go to the 950GB /home partition that I went to all that trouble to set up. I went to copy 59GB of backed up photos into "Pictures" and it said that I don't have enough space. That's wrong - there's basically a TERABYTE where I thought I was putting the files, it's "Free space 39.0GB". 

Do I have to start again? Is it possible that it's mounted the 35GB Xubuntu partition and is using THAT as its "Home"?

I've got 

```
/dev/sda1: UUID="23006707-b8ef-4fed-b235-28593b53684b" TYPE="ext4" <- installed as 15GB /
/dev/sda5: UUID="f6f15efb-3d79-486e-8c1c-23777655af4c" TYPE="swap" 
/dev/sda6: UUID="73611a66-c3d2-4ebb-b6a3-0a063de6286b" TYPE="ext4" <- installed as 950GB /home
/dev/sdb1: UUID="2ec2030a-5ec5-44c7-b251-a3cb78b8d853" TYPE="ext3" <- installed as 2000GB media storage drive

```

---

### Post by ajgreeny on 2014-05-30
There is no 35GB partition listed in your post's blkid? output, so I don't think there is any major problem except that you probably did not set the sda6 partition with mountpoint /home when you installed.  By the way, why are all the partitions you think you have not listed, eg the 35GB Xubuntu partition and the separate ~40GB partition intended for playing around with other linux flavors?

It may be a simple job to edit /etc/fstab to add the /home partition you really want rather than what you have at the moment, but please can you show the full **sudo blkid -c /dev/null** output and also **cat /etc/fstab** and finally **mount** so we know in detail what is present now.  It will also be useful if you can tell us what you think each partition is, ie, your Xubuntu root partition, the ubuntu 12.04 partition etc etc.

---

### Post by evilbrent on 2014-05-30
Thanks,

I was trying to find an output that would list all the drives/partitions/mount points/partition sizes etc all in one place. It's probable that I was confused by the partitions that I wanted/ended up with, it was a long day of installation (spent 8 hours pulling my hair out trying to install 64bit ubuntu onto a 32bit computer:lolflag:) and tried 20 different installations. This final installation that worked I definitely installed "alongside" the Xubuntu I put on to satisfy to myself that it definitely wasn't a problem with the computer and brand new HDD themselves.

There were also historical problems with my setup that required using the text-based alternate install CD for the installation so yes, you may be right, maybe I only MEANT to put /home on sda1

uh........... why isn't /sda1 in fstab at all?? That's odd.

I think that I should be adding this to the fstab?

> # /sda1 to be mounted to /home
UUID=23006707-b8ef-4fed-b235-28593b53684b /home               ext4    errors=remount-ro 0       2

Does that look reasonable?




```
brent@Martha:~$ sudo blkid -c /dev/null
[sudo] password for brent: 
/dev/sda1: UUID="23006707-b8ef-4fed-b235-28593b53684b" TYPE="ext4" 
/dev/sda5: UUID="f6f15efb-3d79-486e-8c1c-23777655af4c" TYPE="swap" 
/dev/sda6: UUID="73611a66-c3d2-4ebb-b6a3-0a063de6286b" TYPE="ext4" 
/dev/sdb1: LABEL="2TB" UUID="2ec2030a-5ec5-44c7-b251-a3cb78b8d853" TYPE="ext3" 

```


```
brent@Martha:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sda6 during installation
UUID=73611a66-c3d2-4ebb-b6a3-0a063de6286b /               ext4    errors=remount-ro 0       1


# swap was on /dev/sda5 during installation
UUID=f6f15efb-3d79-486e-8c1c-23777655af4c none            swap    sw              0       0


# 2TB drive on /dev/sdb1 mounted to /media/2TB_Media
UUID=2ec2030a-5ec5-44c7-b251-a3cb78b8d853 /media/2TB_Media            ext3    defaults 0       2

```

```
brent@Martha:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/2TB_Media type ext3 (rw)
gvfs-fuse-daemon on /home/brent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brent)
/dev/sda1 on /media/23006707-b8ef-4fed-b235-28593b53684b type ext4 (rw,nosuid,nodev,uhelper=udisks)

```
I've also got these two screenshots from Disk Utility which seem useful

[IMG]http://i.imgur.com/Lz40CQ7.png[/IMG][IMG]http://i.imgur.com/tOrZyJt.png[/IMG]

---

### Post by deadflowr on 2014-05-30
I would guess, after creating a home partition, that this would help you out
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
maybe?

As for simply making sda1 the home partition, is anything at all on it?

---

### Post by ajgreeny on 2014-05-31
At the moment sda6 is your root partitiion, ie, the one with the OS on it, and sda1 is just another ext4 partition that should mount if you use nautilus and double click it, though you may find that you can not write to it, depending on what permissions the mountpoint **/media/23006707-....etc etc** has.  You do not have a separate /home partition, so home at present is just a folder within the root partition of sda6.

Follow deadflowr's link and you may be able to get sda1 as your home partition without too much trouble, but make sure you have everything you need backed up as any partition editing always carries a degree of risk; I've never lost anything yet using gparted, but you can bet your boots that if I didn't have a backup, that is the time that it would all go to worms !

---

### Post by evilbrent on 2014-05-31
Yeah I have one backup of the photos, so when the drive died I was down to one copy.

In the end I followed the instructions and moved home ok but when I logged back on it wouldn't log on I think because I didn't have read privileges for the new mount point or some nonsense.

I reinstalled paying more attention top the settings. Quicker and neater.

Thanks.

---

