---
title: "&quot;GRUB Error 18&quot;"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by jclmusic on 2006-07-04
i installed ubuntu 6.06 from the desktop live cd.

after rebooting, i get this error:

"Error 18"

8-[ :-s

---

### Post by MJN on 2006-07-04
Where is your /boot partition? Is your drive big yet your machine old? Older BIOS's often have trouble booting from drives if the bootloaders reside on too high a cylinder number.
 
Solution is relatively simple - create a /boot partition at the beginning of the drive and all should be well.
 
The forum is full of this instance so a search should've revealed the info ('grub error 18' gives 144 hits at the time of writing) - Google on it too if you require further background on the BIOS/HDD side of things.
 
Mathew

---

### Post by jclmusic on 2006-07-04
thanx

---

