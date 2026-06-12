---
title: "Cleaning up Grub2"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by praveenmarkandu on 2009-10-09
my linux kernel is now linux-header-2.6.31-13 and there are a lot of entries in my Grub2 list. is it safe to remove linux-header-2.6.31-11 and linux-header-2.6.31-12 packages as well as the generics?

---

### Post by cariboo on 2009-10-09
Remove the kernels you don't need, I would suggest leaving at least one old kernel, just in case. After removing the old kernels update-grub should run and remove the extra entries from the menu.

---

### Post by emarkay on 2009-10-09
I just remove the kernels and associated files with Synaptic and they disappear for good everywhere.

---

### Post by Vanishing on 2009-10-09
> **cariboo907 said:**
> Remove the kernels you don't need, I would suggest leaving at least one old kernel, just in case. After removing the old kernels update-grub should run and remove the extra entries from the menu.

thats what i always do. but now i have backtrack and vista together with ubuntu, kernel breakage+single kernel won't be such a problem.:P

---

### Post by rburkartjo on 2009-10-09
cariboo tks for the info also good to know

---

