---
title: "Lenovo laptop + win 7 + Ubuntu 14.04. issue"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by tomihau on 2015-11-05
Hello,

I try install Ubuntu 14.04. my laptop with win7 (dualboot). Now I have free space part my /dev/sda prox. 54GB when I use win disktools. Now when I try install Ubuntu (create partition) it says: Cannot create a new partition. There are already four primary partitions.

I think at win 7 and lenovo use all those 4.

How I can continue...

--- 
Tomi

---

### Post by yancek on 2015-11-05
You can't unless you delete one of the partitions and then use that to create an Extended partition on which to install Ubuntu.  Having free space inside a windows filesystem partition won't help as any Linux needs a Linux filesystem to run.  When you boot the Ubuntu installation medium, open a terminal and run this command and post the output here:

> sudo fdisk -l

Lower case Letter L in the command.  You will need to know which partition has the operating system on it, if it has a boot partition and what the other two are.  Probably a Recovery partition and possibly some manufacturer system diagnostics.

---

