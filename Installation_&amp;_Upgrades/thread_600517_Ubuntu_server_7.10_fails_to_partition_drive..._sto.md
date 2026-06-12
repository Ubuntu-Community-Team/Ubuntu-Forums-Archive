---
title: "Ubuntu server 7.10 fails to partition drive... stops at 33%"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by larryroberts on 2007-11-02
Looking for a little help in diagnosing what is going on.  I'm attempting to install Server 7.10 on what is a rebranded Dell PE 650.  Box has the Sil 0680 Ethernet controller (Non Raid version)
Hard drive is a new WD 500Gb EIDE drive. 

Box used to run FC6 and I was able to install FC7 as well.  I would like to migrate this box to Server 7.10 but when I go to do the install, the machine always hangs at 33% when partitioning the HD.  I am wiping the existing partitions and have tried both the guided (whole drive),LVM and manual method.  Machine always hangs at 33% which is formatting / as ext3.  I have left this run for an extended time but it always hangs at 33% and if left long enough (couple hours) it will come back with a error about being unable to complete partition or something (sorry I didn't write it down)

I tried jumping to another shell, but the last message that shows up is about it formatting the swap. 

I'm trying 3 partitions, 1 for /boot at 250Mb, 1 for swap at 1Gb and the rest for /.

Any thoughts on how to diagnose, or should I just grab a standard "non-server" CD and try it.

I know the image/cd is fine as I was able to build a test vmware image without any issues.

---

### Post by louieb on 2007-11-02
Weird! Did you run the check the CD for defects option 1st?
Can't think of any other reason for it not to work. You say the drive is new. May want to run the mfg diagnostic program on it.
Try to set up  your partitions with GParted on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

---

### Post by zub4eg on 2007-11-14
Have same problem.
My configuration:
HDD EIDE Samsung 80 Gb,
Celeron-III 1200, 128+256 RAM

---

### Post by zub4eg on 2007-11-14
Oops.. ))
It looks like CD-RW disc was broken. Burned same ISO to another CDR and partition passes.

---

