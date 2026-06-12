---
title: "Install on 2nd HD"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by DJPlayer on 2008-09-13
Frustrate but here's the gist.  PC is set in Raid0 on 3 raptors.  I have an additional HD for storage and need to use it for ubuntu.  I don't have time to tinker w/ the whole FakeRaid setup.

So I go to install 8.04 on the second HD.  Did a manual install on this drive.  3 Total Partitions.  1 NTFS, 1ext3, and 1 swap.  I then told Ubuntu to install grub on this HD rather than default 1st (which is RAID anyways).  

nada... no Grub loadup.  If I book to windblows and use EasyBCD it still won't allow me even if I try to use neogrub.  I don't think it's finding the grub whatsoever.  I have a couple blunders where I installed grub to the mbr and had to run windows /fixmbr to get everything going again.  Occassionally the install will also wanna turn my raid0 quirkly if it touches the mbr =/

anyone have a good step by step for this.. or can somewhat walk me through?  Not sure if I need to manually edit grub or not.  ugh..

---

### Post by Sef on 2008-09-13
Check out the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

