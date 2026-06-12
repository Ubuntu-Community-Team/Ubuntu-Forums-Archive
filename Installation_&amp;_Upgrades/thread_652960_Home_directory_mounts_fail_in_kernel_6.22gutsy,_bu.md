---
title: "Home directory mounts fail in kernel 6.22/gutsy, but not 6.20"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by philidor on 2007-12-29
I just upgraded a workstation to gutsy from fawn.  It was configured so that my user home directories were on my file server (running the fawn server).  Now when I boot the workstation into the 2.6.22-14-generic kernel, all the fileserver mounts fail (and of course it then hangs).  When I instead boot into the 2.6.20-16-generic kernel, the mounts all work.  The latter informs me that I'm in a "low-graphics" mode, but it's hard for me to accept that a graphics problem is causing a filesystem mount problem.  However, I don't have much depth in Unix, so could be.  I need some hints on where to start.

My workstation is Intel/Nvidia, dual-boot with XP.  The relevant part of my fstab is

# server home directory mounts
192.168.0.1:/  /mnt    nfs4    proto=tcp,port=2049     0       0
/mnt/home       /home   none    bind
   
:confused:

---

