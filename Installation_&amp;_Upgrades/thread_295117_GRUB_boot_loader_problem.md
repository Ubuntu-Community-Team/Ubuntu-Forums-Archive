---
title: "GRUB boot loader problem"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by tehfatal on 2006-11-07
im installing Ubuntu, and am currently at 94% for a while now.  GRUB is tring to be installed to hd0, and it stays at 94% forever.  Im wondering if this is the wrong place for this to be installed, or is it normal for this part to take a while to complete.

thanks.

---

### Post by tehfatal on 2006-11-07
Anyone?

---

### Post by bulldog on 2006-11-07
Nope it's not normal,GRUB should be installed in a second.

Do you have one hdd or more?

---

### Post by tehfatal on 2006-11-07
just one hd.  But i have a duel boot w/ windows xp pro(20gigs), and a storage partition(50gigs), and then the rest is for linux.

During setup i used a 300mb partition as linux-swap type, and then the rest is formated as ext3 for '/'.  Ive installed slack 11, FC6, and Mandriva07 using this sort of partitioning(except without the 300mb for swap) and have had no problems.

But the Ubuntu6.10 install basicly stops at 94% and doesnt move. I know the grub install gets going, bec when i start up after getting annoyed, the boot stops at grub and i cant get into windows or linux(which i fixed so atleast i can get into windows).

GRUB is set to install at hd0, which i dont know if its the right place for it. I want it installed to the MBR, but im not sure if hd0 is the same as MBR.

---

