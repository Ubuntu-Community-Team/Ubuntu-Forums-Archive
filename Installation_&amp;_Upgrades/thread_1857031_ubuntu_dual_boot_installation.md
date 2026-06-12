---
title: "ubuntu dual boot installation"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by tharunkumarkmr on 2011-10-09
hi
i have installed my ubuntu 11.04 desktop edition.i gave the mount point for this as'\'.now i want to install my ubuntu server edition in my system as dual boot mode. i can't able to mount this again from '\'.kindly help me in specifying the mount point.

---

### Post by Basher101 on 2011-10-09
you would need another seperate partition. could you open Gparted from the Live CD session and post a screenshot of your partition table?

---

### Post by MAFoElffen on 2011-10-09
> **tharunkumarkmr said:**
> hi
i have installed my ubuntu 11.04 desktop edition.i gave the mount point for this as'\'.now i want to install my ubuntu server edition in my system as dual boot mode. i can't able to mount this again from '\'.kindly help me in specifying the mount point.
As with other multi-boot systems, you would have to boot from a LiveCD > go into GParted and resize your existing partition to make room for your new install partition.  Having 2 installs of Ubuntu on one disk, you would have to ensure you keep track of what is the controlling Grub when you do updates.

*** Just curious- What is the "purpose" of your 2 Ubuntu Editions?  Are you installing Server to learn the system or for use?  If it is to learn, then you are doing ths right... I learn by doing. If you are doing this for use- that there is some functionality or a purpose that you need to fulfill, then maybe you might be going about this wrong.

For Server to be "working," it needs to be running.  There is a solution where you can have both at the same time (concurrently).  You could install server services such as LAMP onto your desktop edition.  You can do the same by installing a desktop environment package on Server, but the "resource" priorities are different.  (That would be based on what your priorities are... your desktop services or the server services.) I've have both setups here and standalone installs of both.

That way, you can access those services from another PC on your network, or Locally from your desktop through loopback....

Just an observation.

---

