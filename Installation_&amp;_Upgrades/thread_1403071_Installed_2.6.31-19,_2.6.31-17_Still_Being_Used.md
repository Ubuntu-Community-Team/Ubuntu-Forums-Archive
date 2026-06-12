---
title: "Installed 2.6.31-19, 2.6.31-17 Still Being Used"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Cody Larson on 2010-02-09
I upgraded via the Update Manager and saw that a couple of Kernel updates where in there. I just quickly hit update without reading (not the best method, I know). I did remember however it said (New Install) next to the new kernel updates.

Post update I entered uname -r and saw that I am still running -17, however, I have the package installed for -19 when I open Synaptic.

I know that -20 is proposed. What should I do? I am an Ubuntu and Linux n00b.

---

### Post by x33a on 2010-02-09
Somehow grub still points to the older kernel.

you'll have to edit grub to point to the latest kernel (if it exists there). Otherwise you'll manually have to add the kernel entries into grub configuration file.

what version of ubuntu are you using? 9.10 uses grub2 while the earlier versions use grub legacy.

---

### Post by Cody Larson on 2010-02-09
I'm running a clean 9.10 install with GRUB 2. Should I just try a sudo update-grub?

---

### Post by presence1960 on 2010-02-09
> **Cody Larson said:**
> I'm running a clean 9.10 install with GRUB 2. Should I just try a sudo update-grub?

That should work. Next time you do a kernel update make sure you choose "use the package maintainer's version" rather than "use existing version". If you choose to use the existing version your new kernel is not included in GRUB- more specifically grub.cfg

---

### Post by x33a on 2010-02-09
> **presence1960 said:**
> That should work. Next time you do a kernel update make sure you choose "use the package maintainer's version" rather than "use existing version". If you choose to use the existing version your new kernel is not included in GRUB- more specifically grub.cfg

Yes, but if you have made any edits to grub.cfg, then on using the package maintainer's version, they won't be retained. in that case you can try merge.

---

