---
title: "Help with network install"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by lloyd_b on 2006-10-18
I am attempting to install Ubuntu onto a laptop (Sony VIAO PCG-F450) and I'm getting nailed by a pair of problems.

Problem 1:  The machine in question has a somewhat flaky CD-ROM drive.  It reads regular CD's without too much of a fuss, but gives me random errors when I try to read a CD-R.  Net result:  My attempts to install from a downloaded/burned ISO failed miserably.

Problem 2:  The only network adapter I have available for this machine is built into a port replicator (It a KSLI USB ethernet).  I have gotten a network install running on this machine, but it doesn't have the necessary driver for this adapter.

I have a working copy of Debian (Sarge) on this machine.  By grabbing vmlinuz/initrd.gz for the netinstall, I was able to get the network install working (with the above-mentioned problem).

I also had limited success with another approach - unpacking the ISO to an unused partition, and setting GRUB to boot to it.  The install fails when it hits the point where it would mount the CD-ROM.  At that point, I get a shell, and I *can* mount the HD partition at the appropriate mount point (/root/cdrom), but I have no clue as to how to get it to resume the install (I've tried "/init resume", but that still doesn't get anywhere).

I would appreciate any of the following:

1. Instructions as to how to resume my HD install.
 
2. Directions to a netinstall vmlinuz/initrd.gz that contain the necessary USB support.

3. Good instructions for any other method of getting Ubuntu onto this machine.


Lloyd B.

---

### Post by lloyd_b on 2006-10-19
Never mind.

A switch to a different type of CDR disk, and a switch to the alternate install image, and by golly the flaky CD drive on this thing actually managed a clean install...

---

