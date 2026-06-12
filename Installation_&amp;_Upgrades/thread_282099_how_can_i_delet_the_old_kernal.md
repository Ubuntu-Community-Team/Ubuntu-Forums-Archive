---
title: "how can i delet the old kernal"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by abu3abdalla on 2006-10-22
alsalamo alikom 
after i setup the SMP package on my laptop "dual core" it would appeare three kernals in grub screen and happened some problem "not alwayse" in the system so i am decide to delet one of that kernals couse the second kernal in the grub screen is the same of the first one so please advise me and tell me how can i delet that kernals.
thank u all

---

### Post by Najand on 2006-10-22
> **abu3abdalla said:**
> alsalamo alikom 
after i setup the SMP package on my laptop "dual core" it would appeare three kernals in grub screen and happened some problem "not alwayse" in the system so i am decide to delet one of that kernals couse the second kernal in the grub screen is the same of the first one so please advise me and tell me how can i delet that kernals.
thank u all

Go and edit /boot/grub/menu.lst and put # sign before every line of the part starting with title <kernel name you don't need> to the next title....

---

### Post by Kateikyoushi on 2006-10-22
You can remove with synaptic or aptitude the unused kernels,they should appear in obsolate packages. You might want to leave one for backup just in case.

---

