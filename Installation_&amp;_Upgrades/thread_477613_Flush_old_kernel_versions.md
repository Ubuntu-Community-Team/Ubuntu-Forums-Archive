---
title: "Flush old kernel versions?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by grenadier32 on 2007-06-18
OK, here's a question that's probably stupid, but I feel like I have to ask anyway. :-P

Anyway, I've upgraded my Linux kernel several times in the time I've used Ubuntu, and all the old kernel versions are still on the computer (they show up in GRUB's boot menu). I'm aware that I can simply remove the entries by commenting them out or just deleting them from /boot/grub/menu.lst, but is there a safe way to actually remove the old kernel versions? Or are they not actually there?

I'm aware it's unnecessary to remove them, I just feel like I only need one, and I'm scared to actually go in and remove them manually.

---

### Post by merlinus on 2007-06-18
Use Synaptic.  Search for the kernel numbers and headers.

Much easier than doing it manually....

-merlin

---

### Post by Pumalite on 2007-06-18
> **grenadier32 said:**
> OK, here's a question that's probably stupid, but I feel like I have to ask anyway. :-P

Anyway, I've upgraded my Linux kernel several times in the time I've used Ubuntu, and all the old kernel versions are still on the computer (they show up in GRUB's boot menu). I'm aware that I can simply remove the entries by commenting them out or just deleting them from /boot/grub/menu.lst, but is there a safe way to actually remove the old kernel versions? Or are they not actually there?

I'm aware it's unnecessary to remove them, I just feel like I only need one, and I'm scared to actually go in and remove them manually.

Bad idea. If an update goes wrong, you won't have a kernel to boot from. Unless you are pressed for space.

---

### Post by grenadier32 on 2007-06-18
> **Pumalite said:**
> Bad idea. If an update goes wrong, you won't have a kernel to boot from. Unless you are pressed for space.
You're probably right, I just /am/ a little pressed for space on this box, and the current kernel is pretty stable on this machine as far as I can tell. I can keep one back-version just in case, but I've got 5 or 6 installed on here at this point, and it's kind of bothering me. :-P

---

### Post by grenadier32 on 2007-06-18
> **merlinus said:**
> Use Synaptic.  Search for the kernel numbers and headers.

Much easier than doing it manually....

-merlin
If there's in Synaptic, that solves my problem nicely. Thanks. :)

---

