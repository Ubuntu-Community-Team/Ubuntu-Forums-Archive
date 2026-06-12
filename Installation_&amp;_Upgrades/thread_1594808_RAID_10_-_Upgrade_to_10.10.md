---
title: "RAID 10 - Upgrade to 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by cmulcahy on 2010-10-12
OK.  I kind of expected some problems.  :)

Using the documentation here: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) I set up RAID10 (I prefer to refer to it as Raid 0+1 but I'm in the minority).  Life is good.  I ran the upgrade and life is bad.  It's not booting.  

For the life of me, I cannot remember how to get the thing to boot again.  I had an uptime of about 300 days so it's been a while since I set this up.  

Anyone know where a good HOWTO lives to chroot my environment, get mdadm installed, get everything configured for automounting my /dev/md0 and running properly again?  The 
mdadm --assemble /dev/md0 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 
worked like a charm.  

Thanks!

---

### Post by cmulcahy on 2010-10-12
I had a request for info on my post.  I had to run sudo apt-get install mdadm in order to get mdadm on the livecd.

---

### Post by ratcheer on 2010-10-12
> **cmulcahy said:**
> 

....  I set up RAID10 (I prefer to refer to it as Raid 0+1 but I'm in the minority).  



Actually, RAID 0+1 and RAID 10 are different. RAID 10 is the same thing as RAID 1+0.

In RAID 0+1, the drives are striped, then mirrored. In RAID 1+0, they are mirrored, then striped.

In small systems, it makes very little difference. However, in large scale systems, the difference is huge. For example, if a single disk in a 100-disk RAID 0+1 array fails, a 50-disk stripe set has to be recreated before the mirror can be reestablished. But, if it is a RAID 1+0 volume, only the single new disk has to be recreated from its mirror twin disk before the array can be "whole", again.

Tim

---

### Post by cmulcahy on 2010-10-18
[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

That's the magic trick.

---

