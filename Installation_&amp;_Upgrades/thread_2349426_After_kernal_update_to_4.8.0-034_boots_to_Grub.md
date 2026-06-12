---
title: "After kernal update to 4.8.0-034 boots to Grub"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by Jessee on 2017-01-14
Hi all,

After receiving and installing an upgrade from kernel 4.8.0-022 4.8.0-034 I cannot boot directly into Ubuntu, instead I'm given the grub menu, after my monitor telling me that there is no signal.
From here I am able to boot into recovery mode with kernel -034 or boot into the old kernel. 
What I've tried so far is updating my kernel to the latest stable (did not work) and, after that, the latest RC (also did not work).

So I and went looking for log files and found this in the kernel.log:
```
Jan 14 19:15:17 jesse-buntu kernel: [    0.033722] [Firmware Bug]: AMD-Vi: IOAPIC[0] not in IVRS table
Jan 14 19:15:17 jesse-buntu kernel: [    0.033754] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found
Jan 14 19:15:17 jesse-buntu kernel: [    0.033784] AMD-Vi: Disabling interrupt remapping
```

This seems to match with the monitor not getting any input, as I have an AMD graphics card. But I haven't got a clue as to how to fix this problem or what it even is.
Any help would be greatly appreciated :)

---

### Post by Jessee on 2017-01-16
It seems that the error above was not releated.
I am able to boot by adding radeon.dpm=0 as a boot parameter. This is of course fine for now, but how do I boot from a live cd with a non working kernel?

---

