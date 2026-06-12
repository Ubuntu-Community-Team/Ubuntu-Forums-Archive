---
title: "i386 -&gt; K7 kernel broke system!"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by uc50_ic4more on 2005-06-26
Hello -

10 minutes ago, using synaptic, I installed the K7 kernel (2.6.11-1) on my AMD64 machine that was previously running the regular ol' i386 kernel. When I tried booting for the first time after the "upgrade", I am left with my desktop background, blank gray "taskbars" with no icons and an immovable mouse, rendering the system inoperable.

Is there a way to use the live CD to replace the kernel back to the i386? Synaptic did not inform me that the i386 would be removed in the course of installing the K7 kernel - is there a way to specify a kernel at boot time?

---

### Post by mrcbrown on 2005-06-26
[QUOTE=uc50_ic4more]Hello -

10 minutes ago, using synaptic, I installed the K7 kernel (2.6.11-1) on my AMD64 machine that was previously running the regular ol' i386 kernel. When I tried booting for the first time after the "upgrade", I am left with my desktop background, blank gray "taskbars" with no icons and an immovable mouse, rendering the system inoperable.

Is there a way to use the live CD to replace the kernel back to the i386? Synaptic did not inform me that the i386 would be removed in the course of installing the K7 kernel - is there a way to specify a kernel at boot time?[/QUOTE]
 Grub should ask what you want to use at boot, I believe it's hit ESC when the grub loader comes up and you can then select which kernel you want to use.

---

### Post by uc50_ic4more on 2005-06-26
[QUOTE=mrcbrown]Grub should ask what you want to use at boot, I believe it's hit ESC when the grub loader comes up and you can then select which kernel you want to use.[/QUOTE]

Excellent! Thank you *very* much, mrcbrown!

---

