---
title: "How do I install Feisty on an existing logical volume?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by grandpa-geek on 2007-04-24
My system is intended to be triple boot with Fedora, Windows, and Ubuntu.  I set up a 2 GB logical volume for Dapper (6.06) and could never get it to boot because of initrd problems.  I would like to install Feisty (7.04) there.  

I have the alternate CD and tried to do the install.  I can't get past the partitioning section of the install.  I don't want to repartition anything, just to install the software.  When I do something (I'm not sure what) that brings up the installation task list, I pick an item past the partitioning, but it keeps sending me back to the partitioning.  

When I get to the boot issues, I'm using the Fedora installation of Grub and can edit the grub.conf to point to the Ubuntu logical volume when I select Ubuntu in the boot menu.

How do I get to install Feisty on the existing logical volume?

---

### Post by indytim on 2007-04-24
One thing to be aware of by using the manual partition option, for the "/" partition and I believe the swap, after you have identified the correct partition, make sure you have also checked the "format" checkbox or whatever.  The installer will not proceed unless it is allowed to format these 2 partitions.

Hope this helps,

IndyTim

---

