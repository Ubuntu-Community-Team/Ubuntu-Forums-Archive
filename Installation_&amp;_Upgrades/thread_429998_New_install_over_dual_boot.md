---
title: "New install over dual boot"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Ewzzy on 2007-05-01
Ok, I've been using Ubuntu off and on since Breezy.  I have to dual boot Windows to use the Adobe Creative Suite for my school work.  I haven't had much trouble getting a dual boot to work except upgrading always causes issues.  I'd like to do a new install of Ubuntu over my Edgy but I want to keep my Windows install as is.  I'm worried that windows won't boot afterward as I have had that happen before in this situation.  Anyone have any tips?

---

### Post by louieb on 2007-05-01
Should be a piece of cake. I guess your going to use the manual partitioning and install Feisty in the same partitions you are using for Edgy.  Just have  a copy of /boot/grub/menu.lst.  The install will have to over write the MBR to  point to the new stage2 location. But thats the default on both the Live and alternated CD. 

IF the install fails to give you the option of booting window. you can just copy the window entry from you copy of menu.lst. That should remain the same.

---

### Post by Ewzzy on 2007-05-04
Thanks, that helped a lot.  Works just fine.

---

