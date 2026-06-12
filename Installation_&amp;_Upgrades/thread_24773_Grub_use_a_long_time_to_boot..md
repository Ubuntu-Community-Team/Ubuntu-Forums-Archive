---
title: "Grub use a long time to boot."
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by haaglin on 2005-04-08
Hi. I just got my brother to install Linux, but he has a problem with the loading. He has a dual install wih Ubuntu and Windows XP. But after the selection of OS, the loading stops at "loading ubuntu" for a long time, before it continues. Is there any solution for this?

---

### Post by soul_rebel on 2005-04-08
I think that's the kernel, grub has already done its job at that point.
Can't tell you a solution, perhaps try to download the lastest kernel and-or boot in the safe mode from grub. Just a suggestion.

---

### Post by erkki70 on 2005-04-08
Hi,
Try to give more details. :wink:
How long do you mean?
Try to post your dmesg result so people can help better identifying why it takes so long.
Good luck!

Cheers,
Erkki

---

### Post by jdong on 2005-04-08
A quantitative time measure (i.e. Seconds) would be helpful. Some information about the computer's hardware (MHz clock speed, etc) would also be useful. What filesystem are you using (if you didn't specify @ install, it should be ext3).


While at the GRUB menu, press "e" to edit the entry. Take out the word "quiet", then press enter to save, then "b" to boot. You should get more text around the Starting Ubuntu area.

---

