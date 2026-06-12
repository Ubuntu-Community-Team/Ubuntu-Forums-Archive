---
title: "Partition planning, dual-boot + virtualized server"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by inteluser on 2008-06-28
I'm planning to upgrade to a 320GB disk in my laptop, and want to install an (k)Ubuntu+XP dual boot configuration, as well as a smaller copy of ubuntu to use as a server.  I would like to be able to boot XP from ubuntu as a virtual machine, and vice-versa.  Furthermore, the smaller ubuntu server should be able to run virtualized in either desktop OS.  

The reason I want a separate server, instead of just using my main desktop installation of ubuntu, is that I want the server to be available while I'm in windows without having to boot my main installation of ubuntu.

Here are my planned partitions:

--------------

/boot 1GB

Windows:
windows-OS 15GB NTFS
windows-PROG 20GB NTFS
windows-DOCS 10GB NTFS

Ubuntu-desktop
/ 10GB
/var 5GB
/usr/local 30GB
/home 150GB
swap 2GB

Ubuntu-server
/ 5GB
/home 2GB
/usr/local 5GB
/var 10GB
swap 2GB

Reserved ~30-40 GB (depending on "320GB"'s meaning)

-------------------

I don't have a very good scale for the appropriate sizes of the partitions, and I'm not sure if having /var and /usr/local separate from / is a good idea (I've read conflicting reports).  I'd appreciate some guidance.

Jason

---

