---
title: "Mounting an NTFS raid 0 device"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by spliffeh on 2010-12-27
Hi, let's say this system has 3 hard drives. Drive #1 and #2 are RAID 0 and Windows7 lives there. It is a hardware RAID, not software. 

On Drive #3 Ubuntu has been installed using WUBI - it boots up and works okay - but it does not see the RAID array.

Do I just need a linux driver to be able to see & mount my "Windows" RAID0 array? Or is this even possible? Can anyone point me in the right direction?

---

### Post by ronparent on 2010-12-27
I suspect that you have to install dmraid. In an Ubuntu terminal window type 'sudo apt-get install dmraid'. Let us know how you make out.

---

