---
title: "Replace Windows with Hardy-install Question"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Harpoon on 2008-04-23
My laptop has four partions:  Windows, Home, Feisty, Swap in a working dual boot configuration.  I would like to replace Windows with Hardy (no separate home partition) but I am not sure if just a reformat then install from CD will potentially cause problems.  Booting is via GRUB.

Before I potentially trash my only working box, I thought it wise to ask if there were any quirks I need to watch out for.

My guess is that dual booting Hardy and Feisty should not be a problem, but I feel the need to be risk averse.  

Thanks for any replies...

---

### Post by Ub1476 on 2008-04-23
If you want to use Feisty and Hardy in a dual-boot, I would download gparted and configure your partitions from there. The best thing is probably to remove Windows with gparted, then let Hardy install on "most disk space available" (that would be were Windows were before).

I've been running Gutsy and Feisty in a dual-boot before, and this caused no problems. I don't think Feisty and Hardy will either..

---

### Post by Harpoon on 2008-04-23
Thanks UB.  I was concerned more with oossible boot problems -- remnants of windows in the MBR, for example.

Most of the posts on dual booting involve getting ubuntu and windows playing nicely, but I was unable to find anything related to trashing windows for a second linux install.

Once the data are backed up I guess I have no choice but to find out on my own.

Cheers

---

