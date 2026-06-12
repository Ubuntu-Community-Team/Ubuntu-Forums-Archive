---
title: "Info Neede.. XP n UBUNTU..??"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by minhajmsm on 2010-06-16
If someone has installed XP n UBUNTU,,, and if the person wants only XP in the system how can that person keep only XP without loosing any information or even without installing XP again..????  ... this is one thing most of em ask...???

when XP n UBUNTU in separate partitions and installed separately..

---

### Post by bumanie on 2010-06-16
Essentailly - 
A) Delete ubuntu partition/s
B) Insert xp disc and go to console mode by selecting "R" for repair and type FIXBOOT, followed by enter then FIXMBR, followed by enter. Answer 'y' to any questions xp asks and once both commands are completed, grub should be removed from the mbr and windows will happily boot on its own.

---

### Post by minhajmsm on 2010-06-16
thanks a lot for the info bumanie,,, I'll try this tomorrow and get back to you..... hope It'll be a good kick back for those who ask these kind of questions... 

thanks a lot bumanie..

---

