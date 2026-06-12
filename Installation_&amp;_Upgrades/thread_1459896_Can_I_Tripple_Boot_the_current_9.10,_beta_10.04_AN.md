---
title: "Can I Tripple Boot the current 9.10, beta 10.04 AND XP?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2010-04-22
I'm 9.10 day to day with occasional jaunts back into XP (Quicktime, burning CD/DVD media).

I want to install the (perhaps buggy) 10.04 but I just want it to be a separate GRUB menu item, existing on it's own partition.

I'm pretty familiar w/ the manual Ubuntu install but is there any reason this won't work as planned?


berk

---

### Post by lisati on 2010-04-22
My current setup is similar to what you have planned, which sounds do-able. I have Vista & its recovery partition, and, until a couple of days ago, I was dual-booting with 9.04. I then installed the beta1 of 10.04 in its own partition & applied all updates, effectively making a triple boot. Each OS has its own clearly identifiable entries in the grub menu.

---

### Post by TBerk on 2010-04-24
Well, I'm currently in the midst of an attempt myself;

- WinXP SP3 (own Partition)
- 9.10 Ubuntu (sharing /, /swap. & /home Partitions w/)
- 10.04 Beta2 from CD, 

and as I type currently downloading 300Megs plus of patches and updates.

The GRUB menu (so far) seems to have taken it all in stride but during my manual partition resizing (not a requirement btw, just some house cleaning) I induced some reasons to need to run fsck.

Other than the need to wait for the mega-download to finish I'm a happy camper... so far.


berk

---

### Post by mmalone21 on 2010-04-24
It should not be an problem but for the record I am running Lucid exclusively at the moment and have had no major issues.

---

