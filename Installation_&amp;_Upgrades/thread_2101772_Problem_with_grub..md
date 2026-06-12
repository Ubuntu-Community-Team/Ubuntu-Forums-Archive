---
title: "Problem with grub."
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by wmmutch on 2013-01-04
**Help !!   Not software savvy !  ** I'm trying to install Ubuntu 12.04 to dual boot with Win XP sp3+.  I purchased the Official Ubuntu Book and am working from the DVD included with the book which says nothing about dual boot.  After some mistakes I got a fully usable install of only Ubuntu on a test machine.  Now I'm working on a mission critical IBM Net Vista with a P4 1.8gig chip and 512M ram. Two partitions on drive0, an 80 gig hdd,  hold WinXP sys and data.  I partitioned drive1, 120gig sdb, for Ubuntu with sdb1 for \ (root and boot)... sdb3 for \user and two other small partitions totaling 1.5gig for swap  and proceeded to install 12.04. The install seemed to go OK, but on rebooting I can access only the Win XP.  WinXp's disk management utility can see my Ubuntu partitions, but can't read inside them.  The Net Vista BIOS allows me at f12 for choose boot from DVD, disk0 or disk1...both disks lead me to Win XP.   I can boot from the DVD and choose demo mode which allows me to see the file system of the Ubuntu.  I was watching the terminal when Grub2 and other grub stuff got loaded so I know it's there somewhere.   This seems to be a Grub / MBR issue.

My questions at this point are.   1.  how to I get a terminal window while running 12.04 in demo mode from a DVD boot??    (takes forever)   2.  What exactly do I have to do to reconfigure what in order to get the boot option??    It is vital that I not damage access to Win XP...I have a recent full backup on an external drive...but this migration has already cost me two and a half days.

---

### Post by nothingspecial on 2013-01-05
*Thread moved to **Installation & Upgrades**.*

---

### Post by Hakunka-Matata on 2013-01-05
Hi, welcome to the forums.  

Boot to your Live CD--

How to start/open a terminal:
Ctrl-Alt-T

how to reinstall grub2

[https://help.ubuntu.com/community/Grub2/Installing#via_Terminal_Commands]("https://help.ubuntu.com/community/Grub2/Installing#via_Terminal_Commands")

comment: a P4 and .5 GiB RAM may very well deliver slow reactions to commands.  

Good luck

---

