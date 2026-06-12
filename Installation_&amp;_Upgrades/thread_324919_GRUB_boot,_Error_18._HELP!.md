---
title: "GRUB boot, Error 18. HELP!"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2006-12-24
Need help, can't boot into my system due to ERROR 18, I installed Dapper, I using the live CD to log on in this forum. I did a little search about error 18 and this what i found:

ERROR 18:  Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Ihave 80GB on my system!

OK,  now that I found the problem mi question is how to solve it.Here are my 2 possible solution.
1) Try to Update the BIOS.
2) Try to move the boot partition to the front, or at least to the appropriate range.

Since I can't  update my MOBO Bios, cause I using the live CD, my only solution is #2, I know I can reinstall the system again ,but I have important files That I don't want to erase when formatting.

My question is how can I solve this problem, using the live CD.

Please help me!

---

### Post by Sef on 2006-12-24
If you have a usb key, just plug it in and save the files you want to back up to there.

---

### Post by mickbw on 2006-12-24
Did you install to an external USB drive.  If so, I would set the size of the ext1 partition to a smaller size during the install, then increase the partition size after the system is working using the gparted live cd.

---

