---
title: "dpkg error"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by ruddin on 2007-09-23
m new to ubuntu n m getting this error
 dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
i donno wht to do...i have installed ubuntu throuh WUBI...i m no longer able to update or upgrade.....n i get the error tht i m nt the superuser...wht does tht mean??...i guess i m the root user...how do i confirm it??

---

### Post by luisromangz on 2007-09-23
Firstly, It would have been nice that you had written all the vowels, it was a PITA to read.

Your problem has a simple solution, just do what the command output is telling you, in this case

dpkg --configure -a

Of course you have to use the sudo command before that, so you gain root privileges to be able to perform that command.

---

