---
title: "Not the install I expected..."
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by holocron on 2007-07-26
Okay, I just installed 7.04 onto a machine I had an existing install of Win 2k Pro.

I ended up using the alternate install CD and following along one of the dual-boot help websites.

I though I chose to install Ubuntu to the available free space on my first HDD with the Windows install. Evidently, I chose wrong.

My system had the following:

HDD#1: Windows and 4GB unallocated space
HDD#2: 8GB unallocated space and several partitions for windows
HDD#3: one big 12gb windows partition

What I ended up with was Ubuntu installed on the entire HDD#2 and the windows partitions on that drive were incorporated into the Ubuntu partition as new "vfat" volumes.

Just for curiosity, what did I do wrong?

But, the point of this post is that I don't really care they are nor Linux volumes. I do want, however, to be able to access them from another Windows machine on my network. Can someone confirm if what I need to do is install SAMBA and then share them out. Then my other windows machines on the network can access them? Right?

---

### Post by Pumalite on 2007-07-26
For Linux to Windows= Samba. For Linux to Linux you could use openssh ( installed through Synaptic )

---

### Post by raja on 2007-07-26
Looks like you chose the second hard drive to install Ubuntu in the free space.
You are right - it is pretty straightforward to setup networking with a windows pc once you have samba.

---

