---
title: "Install Ubuntu on ZFS"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by rock freak on 2013-01-24
Objective:
Install Ubuntu onto ZFS pool.

I have found numerous guides on the interwebs but alas none of them have worked for me yet.

I was wondering if anyone on here has had experience in this before?

The ZFS Pools are all setup and ready to use. I can get ubuntu to talk to the ZFS when it's on a normal install/live disc.

What I can't seem to do is work out how to install Ubuntu by chrooting into the pool. Then patching grub with appropiate files to enable a boot into a zfs bases ubuntu.

I hope that made some sense to someone!

---

### Post by tgalati4 on 2013-01-24
And why is this a good idea?  Normally you would use ext4 for your boot partition and then create data partitions and use zfs for protection of the data partitions.  The overhead of zfs and the fact that it is not the native file system in linux will leave you with an oddball system.  It can probably be done, but if you have issues, where will you get technical support?

---

### Post by rock freak on 2013-01-24
My logical thought was if I could have ubuntu installed on a mirrored zfs array it would make it more stable from corruption?

---

### Post by matt_symes on 2013-01-24
Hi

As for your second issue with grub, have you seen this ?

[https://launchpad.net/~zfs-native/+archive/grub](https://launchpad.net/~zfs-native/+archive/grub)

I have no experience with it but was thinking of doing something similar to what you are doing to play with different filing systems.

Out of interest, what problems are you having when you chroot ? Error messages ? I take it, it cannot read the filing system within the chroot ?

Have you come across this guide ?

[https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem](https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem)

It's what i was thinking of following and uses debootstrap.

Just to let you know that i have no experience with zfs but i was thinking of playing with it myself.

Kind regards

---

### Post by rock freak on 2013-01-24
> **matt_symes said:**
> 
Out of interest, what problems are you having when you chroot ? Error messages ? I take it, it cannot read the filing system within the chroot ?

Have you come across this guide ?

[https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem](https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem)

It's what i was thinking of following and uses debootstrap.


That the guide I was using. I just can't seem to get it to boot into grub! let alone ubuntu!!! I follow it to a T but just can't get it to work!

Might just have to settle for a normal ubuntu install then mount /home/<username> to a zpool have one for each user then.

I can get ubuntu to read/write the zfs filesystem thats not a problem! quite easy infact!

---

### Post by matt_symes on 2013-01-24
Hi

I'll have a go at setting ZFS up on a spare partition i have kicking about and, if i can, i'll install Ubuntu to that partition. If i can get it to work, i'll post back. 

This will be over the weekend though. I plan to have a play with both ZFS and BTRFS in the next couple of weeks.

If i can get it to work, i'll let you decide whether it's the right filling system for your root partition or not.

Kind regards

---

### Post by tgalati4 on 2013-01-24
ZFS has a lot of neat features and you can play with it by setting up freenas, nas4free, or a pcbsd system and mount the drives and use them for rsync backups.  I think it's way too early to rely on ZFS as a main file system for Ubuntu.  It took several years of tuning ext4 before it became a mainstream file system.

If you do get it running, please post your procedures and experiences.

---

### Post by rock freak on 2013-01-25
I need to learn how to setup grub manually on a partition and how to install ubuntu manually via debootstrap!

Once I've masted them I should be able to install onto a ZFS drive.

Anyone know of any good tutorials for the above?

---

### Post by drdos2006 on 2013-01-25
I used this tutorial and made some other notes.

[http://liberumvir.com/2012/06/01/zfs-and-dtrace-running-on-ubuntu.html](http://liberumvir.com/2012/06/01/zfs-and-dtrace-running-on-ubuntu.html)

Firstly, ZFS
1) Install an Ubuntu server. (I recommend trying it out on a VM first.)
2) Attach 2 drives to use for testing ZFS. (Again, I was using a VM, so this was as simple as “attaching” two more virtual hard drives.)
3) Partition the new drives. I used cfdisk on my two newly attached drives. If you aren’t sure of which /dev/sdx device the new drives attached as, just “cat /proc/partitions” and you should find it.
4) Do a “sudo apt-get update && sudo apt-get upgrade” to make sure your system is up to date.
5) Install the needed prerequisites with “sudo apt-get install python-software-properties bison flex build-essential libelf-dev zlib1g-dev libc6-dev-i386 libdwarf-dev binutils-dev”
6) Add the zfs-native apt repo with “sudo add-apt-repository ppa:zfs-native/stable”
7) Update apt with the new sources from the zfs repo with “sudo apt-get update”.
8) Install ubuntu-zfs with “sudo apt-get install ubuntu-zfs”
9) Create your new zpool with “sudo zpool create zfs-volume raidz /dev/sdb1 /dev/sdc1”. Here, “zpool create” is given the name for the pool “zfs-volume” and told to use “raidz” (which will mirror, in this example) and then told to use the two disks we attached and partitioned earlier “/dev/sdb1 /dev/sdc1”.
10) Check out your new zpool with “sudo zpool status”
11) Check out your zfs-blog dataset with “sudo zfs list”
12) See that it is listed with “df -h”
13) Enjoy ZFS running on your Ubuntu server.

For an existing pool, use “sudo zpool create -f ….”, to delete an existing pool, use “ sudo zpool delete zfs-poolname”.

For three (3) drives with an existing zfs-poolname, use “sudo zpool create -f zfs-poolname raidz /dev/sdb1 /dev/sdc1  /dev/sdd1”.

Add “zfs-fuse” module to Webmin, install nfs-kernel-server  nfs-common to Ubuntu, create and share folders under “zfs-volume”, edit /etc/exports for NFS shares. 

I nstalled Ubuntu server on a smaller HDD (Western Digital RAPTOR 37 Gigs) and use 3 x 500 Gig drives for the z-pool.

When I disconnected the second drive of the pool for testing I found I could not access the zfs-pool and there does not seem to be a WebGUI to allow easy changes, or to indicate if the HDD is nearing the end of its life as Nexentastor WebGUI allows. 

For a ZFS server I am leaning more towards Nexentastor rather than Ubuntu.

regards

---

### Post by darkod on 2013-01-25
I don't have much ZFS on Ubuntu experience myself, but if I can help shorten few steps that drdos posted.

For prerequisites I found that only installing python-software-properties is enough, and you need that only because the add-apt-repository depends on it.
Once you have the repo added, doing the install ubuntu-zfs is pulling everything it needs.

Also, you have to use the 64bit version, it won't work on 32bit.

I agree with the idea of having ubuntu installed on ext4 disk (partition), and use ZFS for the data storage. For further redundancy, use raid1 for the ext4 OS disk if you want to.

On my short test it worked very easy, once I figured out I need to use 64bit.

---

