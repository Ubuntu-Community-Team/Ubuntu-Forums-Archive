---
title: "grub nowhere to be found, ubuntu won't load"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by xster on 2006-09-15
I tried installing both in a second physical drive and in a partition of the physical drive that has the original mbr. In both cases, after install, the system goes straight into windows. No grub, no linux. If I force my computer to both to the second physical drive, it will give an error 22 from grub. It was giving me error 22 all the time the last time I tried installing Ubuntu and I gave up. My new tries didn't yield better results.

System commander completly destroys my computer, I had to fixmbr to get windows back.

How do I get ubuntu installed?

If I put it in a partition with windows xp, do I put linux in a primary partition or in a logical partition?

I have windows in a SATA and linux in SATA and IDE and neither work. Help

---

### Post by wieman01 on 2006-09-15
Have you got "system commander" installed while trying to run Ubuntu & installing GRUB? That could be your problem... "system commander" occupies the MBR and locks it for other boot-programs.

---

### Post by xster on 2006-09-15
No, I started looking for other boot managers to start up linux after it failed to load.

---

