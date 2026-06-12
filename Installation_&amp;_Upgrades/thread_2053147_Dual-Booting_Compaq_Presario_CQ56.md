---
title: "Dual-Booting Compaq Presario CQ56"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by djsamrook on 2012-09-04
hey, i am trying to dual boot my laptop so i can have ubuntu and windows 7 running alongside each other. i have deleted the 'hp_tools' partition in windows and shrunk the 'C:' partition so i had a partition to install ubuntu on, but when i go to install ubuntu, it says there is an extra partition that is 1mb in size, with a flag of system, and the drive i created is recognized as unusable data! what should i do? do i just delete the 1mb partition in ubuntu then install or what?

---

### Post by darkod on 2012-09-04
Boot with the cd in live mode first, open terminal and post the output of:
```
sudo fdisk -l
sudo parted -l
```

Note: The parameter in those commands is small L, not the number 1.

---

