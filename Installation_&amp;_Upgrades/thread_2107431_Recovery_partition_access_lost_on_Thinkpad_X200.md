---
title: "Recovery partition access lost on Thinkpad X200"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by Vignesh Sankaran on 2013-01-21
After I installed Ubuntu dual boot with Windows XP, I realised that the F11 went missing. I have seen tutorials to address this with GRUB, but I'm on 12.04 which uses GRUB 2, and I'm struggling to get it to appear again.

---

### Post by Mark Phelps on 2013-01-22
What you probably mean is that pressing F11 no longer brings up a Recovery option, right?  

IF your recovery partition got clobbered as part of your Ubuntu install, there is no way to get it back.

To see if it is still there, open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.  That will list out the partitions on your drive and allow us to see if the former Recovery partition is still there.

---

