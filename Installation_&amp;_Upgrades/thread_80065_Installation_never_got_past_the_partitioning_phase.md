---
title: "Installation never got past the partitioning phase"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by vtqanh on 2005-10-21
I tried to install Ubuntu last night for more than 4 hours and still could not figure out what the problem was. It kept getting stuck at the partitioning phase. I have a Maxtor SATA HDD 80GB. If I let Ubuntu to decide the partitioning, which came out to be 76GB in ext3 (for / and home) and 1.5GB for swap, the installation would freezes about 20-30% while trying to partition the disk (it says creating the ext3 on ....). If I choose 5GB for / and 1 GB for swap, and just leave the rest unallocated, it would go to 100% and stays right there forever.
There is absolutely no problem with the HDD, I just took it to my windows box and did a full format (not a quick format), ran a full scan for error (no error at all)
Any suggestions?

---

### Post by davmac on 2005-10-21
I had problems installing ubuntu on my son's Dell Dimension with 160Gb SATA drive. To fix it I had to change the bios setting for the drive to "compatibility mode" and everything worked ok from then on.

HTH,

Dave Mac

---

### Post by vtqanh on 2005-10-21
[QUOTE=davmac]I had problems installing ubuntu on my son's Dell Dimension with 160Gb SATA drive. To fix it I had to change the bios setting for the drive to "compatibility mode" and everything worked ok from then on.

HTH,

Dave Mac[/QUOTE]

I dont see a similar option in my BIOS. What does compatibility mode mean?

---

