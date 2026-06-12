---
title: "Upgrading a server with RAID arrays to a desktop"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by dessertfirst on 2017-02-14
I run a small home LAN file server (SMB) which I also do occasional development work on. A desktop GUI environment is a necessity. I've had such a machine running for years but recently needed to upgrade the 2TB disks to 4TB disks. Due to the size of the new disks I've had to use GPT partitioning and trying to get such drives setup with a RAID1 (software RAID) configuration has been trying. After over a week of trying to do this using my old Centos 6 distro, I decided to give up and see if Ubuntu could offer me something. Somewhere I read that the installation disk of Ubuntu Server would allow the setup I desired. Lo and behold it does! I have created a bootable Ubuntu 16.10 server with exactly the RAID setup I need. Now, I have two main problems to solve ... putting a desktop environment on the system, and copying a few terabytes of data from my old disks to the new system. My question is mainly about the former. I thought maybe I could download the Ubuntu Desktop and "upgrade" the server to include the desktop environment I need. (BTW, I forgot to mention I'm trying this with Ubuntu 16.10) This didn't work as the desktop installer doesn't recognize my RAID arrays. I could look at another running desktop and try to put those packages on my system with apt, but that sounds terribly time consuming. I'm not familiar with the Ubuntu package names as I come from a Centos/Redhat environment. Any suggestions on how to get to my target environment? Maybe there is a desktop installer that will allow me to do the RAID setup? At this point I don't particularly care what version of Ubuntu I run, an older version would be fine as well.

Thanks!

---

