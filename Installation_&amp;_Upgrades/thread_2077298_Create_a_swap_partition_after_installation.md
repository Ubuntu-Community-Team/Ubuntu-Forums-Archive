---
title: "Create a swap partition after installation"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by aigljd on 2012-10-28
Hi guys,

I'm new to the world of ubuntu and I have yet to solve some issues to get my OS fully working : I don't know if it is linked but as I don't currently have a swap-linux partition, my sleep/suspend and hibernate functions do not work.

Consequently, I have three questions :)

1) How to create a swap partition after installation, knowing that I already have 4 primary partitions (I can't create any) and that I would like to use 15GB of unallocated space as a swap partition. 
Here is my HD is partitioned : 
SDA1 : boot
SDA2 : win7
15GB unallocated (to be mounted as swap partition)
SDA3 : Ubuntu
SDA4 : Samsung Recovery

2) How to enable sleep/suspend ?

3) How to enable hibernate ?

I'm on Ubuntu 12.10 w/ Gnome environment.

Thanks a lot for yout help :)

---

### Post by darkod on 2012-10-28
On a hdd with msdos partition table there is no way to create new partitions when you have existing 4 primary partitions.

There is a program called fixparts that is able to convert a primary partition into logical. I would try to convert the root partition you have (/dev/sda3) into logical, and that would allow you to create another logical from the 15GB unallocated space if it's position immediately before /dev/sda3 as you say it is.

Note that changes like this have a certain amount of risk, so you should have a full backup before trying this. I have never used fixparts, but I have seen on it's website that it has ability to convert to logical. Read carefully the instructions on the website:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Once you have the swap created, you will have to add it to /etc/fstab but that's easy. We can give you instructions once you are there.

Also, once you have the swap partition I think hibernate will work by defauls. Now it doesn't work since the swap partition is where it saves data so it can hibernate.

---

### Post by aigljd on 2012-10-28
Ok finally I decided to reinstall ubuntu from scratch, I created a extended partition then added a swap-linux partition via gParted after the installation.

How do I tell Ubuntu to mount it and use it as its swap partition ?

Thanks ! ;)

---

