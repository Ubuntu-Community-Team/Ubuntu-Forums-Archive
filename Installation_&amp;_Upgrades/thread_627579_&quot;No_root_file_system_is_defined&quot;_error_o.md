---
title: "&quot;No root file system is defined&quot; error on install"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by billeg on 2007-11-30
Hello;

I have a dual-boot XP/Vista system, and I am trying to install Ububtu from the "live" CD.  

I have the following partitions shown in the "partition editor":
/dev/sda1  ntfs  xp    117.19 GiB
/dev/sda2  ntfs vista 105.93 GiB
/dev/sda3 ext3             3 .91 GiB
/dev/sda4 ext2             5.86 GiB

Sda3 and sda4 were partitioned using the Ubuntu partition editor.  I located a post that said these should be setup for use by Ubuntu, and that the base partition needed to be about 2 GB (ext3), I believe, and the swap partition needed to be about 1 GB (no type specified).

The error indicates that I need to have a root "/" specified.  However, I can't find any help posts addressing how to do this.  Can someone point me to where/how I can do this specification?

Am I on the wrong track?  Does the Ubuntu partition need to be before the XP/Vista partitions?  Do I need to partition using something other than the Ubuntu partition editor?  If so, what should I use?  Are there any issues with having a tri-boot system.

My initial goal is to be able to pull mixed-case files from a UNIX repository into Windows after cleaning the names up using a compliant operating system.  I have a large repository of archives that are useless because the checkin/checkout fails due to the mixed-case filenames being "ambiguous".

Thanks for any help.

---

### Post by Pumalite on 2007-11-30
How did you make those ext3 partitions? When using Vista you have to allocate space for Ubuntu from Vista partitioner. I'd allocate at least 15 GB. 10 for '/' alone, 50 MB /swap and the rest for /home.

---

### Post by billeg on 2007-11-30
I made the two non-windows partitions using the "live CD" disk partitioner.

When I make the partitions from Vista, should both be ext3?  If I want to share between windows and Ubuntu, what do I need to do?

Thanks, Bill

---

### Post by Pumalite on 2007-11-30
If you can, make the new partition ext3 and install Ubuntu. Go Manual and follow my instructions.

---

