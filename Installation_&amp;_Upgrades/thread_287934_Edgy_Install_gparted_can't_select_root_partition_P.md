---
title: "Edgy Install gparted can't select root partition Problem Solved"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Seattle_Mike on 2006-10-29
I have 2 Sata and one Pata dirve and Edgy install gparted recognize all my drives but doesn't let me get past the selection of root partition with "/".

I installed Edgy beta a few months ago and it was fine on this system.

ASPUS P4P800, 1GB Ram, 2x120 Sata, 1x200 Pata, ATI Display. 

FWIW - Dapper runs AOK on this system.

---

### Post by Seattle_Mike on 2006-10-29
SOLVED:  After reading other posts thinking it was for betas, I said why
not and I got Ubuntu installed properly. 
Fix is to use gparted as a standalone, delete the partition you want to install on, then recreate.   "Magically" the Installer gparted will then
pick that recreated partition as root partition and will proceed. 

It works but like others say ... That's an bad introduction for new users.

---

