---
title: "New server installation reboots"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by revdave on 2006-10-26
After running Debian for years I switched to Ubuntu a few months ago to run a small LAMP+ server. The other day, one of my two aging hard drives decided to go kathunk-kathunk. It was housing my /usr directory tree. So I have been trying to get things going with a little extra space I could find on my other hard drive (2G free space) until a new hd arrives that I ordered. (not sure when that will be, hopefully soon, but I know I have email waiting for me and others)

Problem is, I cannot get a good boot into the ubuntu server. I have tried both the Edgy and the Dapper server (i386) cds. They run fine and set things up, but when it comes to rebooting the new partition, it immediately reboots. I watch the messages and it says either "Starting up..." (Edgy) or "boot" the very second the machine reboots.

The Dapper Live CD works just fine. I can see and move around the partitions that it is trying to read. The installation routine saw the old Debian root and makes it a grub menu. Choosing that will run that kernel until it freezes (another problem that the reinstallation is supposed to fix (I tried just copying that kernel to the partition I want to boot to which showed the kernel problem), and the memtest option runs fine. 

I have a Asus P5a Super7 Motherboard. The hard drive is a Maxtor 8.5G. It has only run a lilo booted debian (untouched by M$)

The grub menu.lst looks like it should look [root (hd0.0) and /dev/hda1 as the location of the boot and initrc images]

What am I missing? ](*,) 

Next step is to install lilo if it is a grub issue, but since grub appears to work elsewhere, I'm not sure that is the problem.

---

### Post by az on 2006-10-26
> **revdave said:**
> After running Debian for years I switched to Ubuntu a few months ago to run a small LAMP+ server. The other day, one of my two aging hard drives decided to go kathunk-kathunk. It was housing my /usr directory tree. So I have been trying to get things going with a little extra space I could find on my other hard drive (2G free space) until a new hd arrives that I ordered. (not sure when that will be, hopefully soon, but I know I have email waiting for me and others)

Problem is, I cannot get a good boot into the ubuntu server. I have tried both the Edgy and the Dapper server (i386) cds. They run fine and set things up, but when it comes to rebooting the new partition, it immediately reboots. I watch the messages and it says either "Starting up..." (Edgy) or "boot" the very second the machine reboots.

The Dapper Live CD works just fine. I can see and move around the partitions that it is trying to read. The installation routine saw the old Debian root and makes it a grub menu. Choosing that will run that kernel until it freezes (another problem that the reinstallation is supposed to fix (I tried just copying that kernel to the partition I want to boot to which showed the kernel problem), and the memtest option runs fine. 

I have a Asus P5a Super7 Motherboard. The hard drive is a Maxtor 8.5G. It has only run a lilo booted debian (untouched by M$)

The grub menu.lst looks like it should look [root (hd0.0) and /dev/hda1 as the location of the boot and initrc images]

What am I missing? ](*,) 

Next step is to install lilo if it is a grub issue, but since grub appears to work elsewhere, I'm not sure that is the problem.

Is it a pentium one processor?  The server kernel does not boot on anything less than a 686 (pentium II).  You may boot the alternate cd and chroot into your install.  You can then install the desktop kernel (linux-image-386...)

Or you can just reinstall from the alternate cd (which installs the desktop kernel and not the server kernel - even when you boot with the server install option) and install LAMP afterwards.

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by revdave on 2006-10-26
That was the key. Thank you! :p 

I think maybe a little more information out there on what is meant when it talks about "server kernel". If it was there, I missed it.

Actually, the solution was simpler than downloading another CD image (especially the day after a new release). I ran across it accidently, but I should have remembered about the virtual console. (I usually telnet in and don't physically interact with the server much).

I ran the server installation CD and when it asked if I was ready to reboot, I moved to the virtual console (Alt-F2), then chrooted to the new installation and ran apt-get from there.

chroot /target /bin/bash
nano /etc/sources.list (to take out the reference to the CD Image)
apt-get update
apt-get install linux-image-386

I removed the server kernel just to clean it up a little bit, but that wouldn't be needed to get things running.

When that was all done, I went back to the first virtual console (Alt-F1) and Continued the installation process.

Good thing no one was home when it did that, they would have wondered what all the hooting and hollering would have been about.

---

