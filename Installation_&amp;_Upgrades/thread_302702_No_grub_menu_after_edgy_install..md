---
title: "No grub menu after edgy install."
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by Jamie Jackson on 2006-11-19
I installed Edgy, but I don't get the OS choice on boot; it goes straight to WinXP.

I guess I installed grub on the wrong partition??

How can I fix it? FWIW, I've got lots of tools at my disposal (Super Grub boot CD, Knoppix Live, Ubuntu Live, System Rescue CD.)

Also, how can I double check that the grub notation I guessed (hd0,1) actually corresponds to my target partition? Is there a way to browse the partitions by grub notation?

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-19
Oh, and if you're wondering why I didn't install in (hd0) (MBR), it's because [this guy told me not to on his site]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/"), and I don't know any better.

---

### Post by funkyade on 2006-11-19
hiya,

I posted some instructions for a similar issue on the following thread yesterday, check them out, it may help -

[http://ubuntuforums.org/showpost.php?p=1774972&postcount=2](http://ubuntuforums.org/showpost.php?p=1774972&postcount=2)

---

### Post by Jamie Jackson on 2006-11-20
I think there were two problems: I think I installed grub to (hd0,1) instead of (hd0,2), and I don't think (hd0,2) was the active partition.

I reinstalled grub to (hd0,2), but that didn't work (still went straight to XP on boot).

Then, using the Super Grub boot disk, I set the active partition to (hd0,2), and that did the trick.

Thanks,
Jamie

---

