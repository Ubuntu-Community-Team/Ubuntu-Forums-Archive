---
title: "Mass Linux installations - how to go about it"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by Nicolai on 2005-09-20
When we installed Ubuntu in our network of 32 computers, we did it via CDROMS. 

It's time consuming, and I think there are better ways out there which I may not know yet. I've been thinking, what are the other ways of  deploying Ubuntu (or Linux, in general) which wouldn't require CDROMS or the Internet.

Experts, what do you think?

There's kickstart, for one.

 How about [installing from the network](http://www.linuxplanet.com/linuxplanet/tutorials/986/3/) ? with 100mbps LAN cards and switches, would this be faster?

---

### Post by Nicolai on 2005-09-20
OH, oh, oh.

It says in the Ubuntu 5.04 release notes that ...

Installing Ubuntu

Kickstart Compatibility

    Ubuntu 5.04 introduces Kickstart compatibility so that a system administrator can define install parameters once, and then install Ubuntu on a **number of machines via CD-ROM, local hard drive, NFS, FTP, or HTTP.**

Now, where's that howto ..

---

### Post by aysiu on 2005-09-20
Or you could use [PartImage](http://www.partimage.org/), which says it's useful for this reason: *This utility can be used to install many identical PCs. For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function.*

---

### Post by macgyver2 on 2005-09-20
[QUOTE=Nicolai]Now, where's that howto ..[/QUOTE]
[Here's something](https://wiki.ubuntu.com/KickstartCompatibility)  from the wiki.

---

### Post by GOwin on 2005-09-20
This sounds interesting. 

Has anyone actually configured a quick and dirty DHCP/NFS/Kickstart  server for such an installation process?

This sounds good for corporate network migration.

Partimage may be good IF you use the same brand/model of computers in your network. The Kickstart/NFS solution sounds more flexible.

---

### Post by macgyver2 on 2005-09-20
[QUOTE=GOwin]Partimage may be good IF you use the same brand/model of computers in your network. The Kickstart/NFS solution sounds more flexible.[/QUOTE]
You still may need to work around a couple things.  For instance, different computers probably means different X configs and possibly different partitioning.

---

### Post by GOwin on 2005-09-20
So, how does one go about setting up such an NFS server?

Linux n00b here. :D.

I'd like to try it out.

---

