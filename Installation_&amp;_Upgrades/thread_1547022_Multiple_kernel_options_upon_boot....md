---
title: "Multiple kernel options upon boot..."
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2010-08-06
Hi all,

I have a dual boot PC, with Ubuntu Lynx & XP installed. I've also installed (under Ubuntu) start-up manager as well.

My problem is that now I have multiple kernel options to choose from before I get to XP (which I don't use often, but when I do I don't want to be scrolling for ages to get to it).
 
Is it possible to list only the latest installed kernel and XP as options? And, if so, how would I go about doing this? Is there a better program than start-up manager that will give me some flexibility to delete earlier kernels from the boot menu?

Thanks in advance,
Baldrick.

---

### Post by rohit raj on 2010-08-06
I have also the same problem

---

### Post by Pablo Pablovski on 2010-08-06
Depending on how many kernel options you wish to have (I'd suggest at least two - current and last, in case you hit problems with the newest one), you could simply uninstall the oldest kernels in Synaptic - that will force a re-register of the remaining installed kernels and update to GRUB accordingly, so you end up with just, say, two kernels (and MEMTEST, which can be deleted from GRUB - see instructions elsewhere), plus Windows.

That's what I do, anyway.

EDIT: There's an excellent GRUB2 config guide here:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

