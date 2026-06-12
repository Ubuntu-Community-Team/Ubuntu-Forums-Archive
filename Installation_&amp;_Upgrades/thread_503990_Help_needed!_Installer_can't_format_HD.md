---
title: "Help needed! Installer can't format HD"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by bogoliubov on 2007-07-18
I am trying to install Xubuntu 7.04 onto a standard PC. This computer has had Ubuntu on it before, so there should be no problems with hardware compatibility.

After having set up the partitions, the installer tries to format the HD, but fails for some reason. I have no idea why. Just to test I dug out some old Fedore Core 2 CDs from my closet and tried these. The installer told me there was some problem with the partition table, but I could proceed and everything went OK. So the HD seems to be OK, but I can't install Xubuntu! 

Any ideas are greatly appreciated!!

---

### Post by bogoliubov on 2007-07-18
I just tested with an old Dapper Live CD, and it seems to work there as well. So what is the problem with the Xubuntu 7.04 CD???

I reburned (it an CD-RW) the CD at a lower speed and used the verify data option (in OS X Disk utility), just to make sure the CD is OK..., still the same problem...!

---

### Post by bogoliubov on 2007-07-19
Bump...

---

### Post by merlinus on 2007-07-19
Post system specs.  Is windows installed on one of the partitions?

You might also try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by bogoliubov on 2007-07-19
> **merlinus said:**
> Post system specs.  Is windows installed on one of the partitions?

You might also try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

AMD Athlon XP 2600
1 Gb RAM
Geforce 6200 (AGP)
80 HD
No windows installed!

I can post more detailed specs when I get home from work.
By the way, I tried gparted from within the LiveCD, but it keeps automounting the drive so I can't format it. Can I stop it from automounting?
I'll test gparted live when I get home, thanks!

---

### Post by bogoliubov on 2007-07-19
> **merlinus said:**
> 
You might also try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin


I tried it and removed all partitions from the drive, then created a new ext3 partition. Everything went OK. Then I tried the Xubuntu LiveCD again, but I still get the same error! This is really frustrating!

---

### Post by bogoliubov on 2007-07-20
As a last resort I'll try to install Xubuntu 6.10 and then upgrade to 7.04. Hope that works..., really annoying problem!

---

