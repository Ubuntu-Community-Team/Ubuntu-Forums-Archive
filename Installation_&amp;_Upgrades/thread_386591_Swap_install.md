---
title: "Swap install"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by gm__ on 2007-03-17
Why can i install Ubuntu without swap on my desktop and not on my laptop?
Both have 1024 Ram, which means it's enough memory so i dont need swap.

---

### Post by Kateikyoushi on 2007-03-17
Because hibernation writes to the swap partition.

---

### Post by gm__ on 2007-03-17
Thanks a lot Kateikyoushi , but on desktops there is hibernation too.

---

### Post by Kateikyoushi on 2007-03-17
Honestly I was under the impression that the installer requires minimum 256Mb swap. 

I can only think that on the desktop hibernation is not enabled by default so it was not a requirement.

Did you use the same disc and same install method both times ?
By the way you do not loose performance with enabled swap, you have data which can be dumped right after the boot because it won't be used till you shut down, also linux swap can be twekaed how much do you want to swap and what do you want to swap. There is no real gain in not using it, and I did that for 2 years on my notebook.

---

