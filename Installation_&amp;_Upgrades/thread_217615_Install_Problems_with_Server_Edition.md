---
title: "Install Problems with Server Edition"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by bwiewiora on 2006-07-17
I'm trying to install Ubuntu server 6.06 edition on an old Dell PowerEdge 2400 (PIII, 667 mHz, 256 megs RAM), and I'm running into a peculiar problem.  I made the cd with the ISO, and it starts to boot from it, but then restarts the system before the installation starts.  This goes in an endless loop so there is no way to start the installation.  I think it has something to do with the SCSI cd drive or the RAID, but I'm not sure.  I unfortunately don't have any of the other specs for the machine--it has no OS currently.  

I've been trying to find a way to boot it from a floppy and then access the ISO directly, but I can't find any program that will run an ISO.  Any other suggestions?

Thanks in advance

---

### Post by maguns on 2006-09-12
I've got (probably) the same problem. When I try to install with debug options in the terminal window the server ends up with a kernel panic.... Something with "could not open adapter...." I wonder if it has to do with the drivers of the SCSI CD?
Are we alone in this or are we just using to old Dell servers??

/Magnus

---

