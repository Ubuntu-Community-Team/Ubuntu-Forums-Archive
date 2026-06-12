---
title: "getting grub to boot winXP on separate HDD"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by mistafeesh on 2007-07-23
Hi,
Due to some hardware issues, I've had to temporarily put my kubuntu 7.04 and windows XP drives in the same computer. Both boot fine and work well (I had to reconfigure X, but apart from that it all worked). I've tried a few times to add windows XP into the grub menu without much success.

From ubuntu, the windows drive shows up as hdb1. It's currently slave on the first IDE bus, and ubuntu is master on the same. AS far as I can tell, in the language of grub that makes windows hd0,1 (although I've tried a good few permutations!) Basically, it looks like it's booting but then just sits there doing nothing.

Is there a way I can either get grub to re-autodetect the windows drive or install it to the windows drive?

---

### Post by confused57 on 2007-07-23
> **mistafeesh said:**
> Hi,
Due to some hardware issues, I've had to temporarily put my kubuntu 7.04 and windows XP drives in the same computer. Both boot fine and work well (I had to reconfigure X, but apart from that it all worked). I've tried a few times to add windows XP into the grub menu without much success.

From ubuntu, the windows drive shows up as hdb1. It's currently slave on the first IDE bus, and ubuntu is master on the same. AS far as I can tell, in the language of grub that makes windows hd0,1 (although I've tried a good few permutations!) Basically, it looks like it's booting but then just sits there doing nothing.

Is there a way I can either get grub to re-autodetect the windows drive or install it to the windows drive?
Maybe you can use the Windows entry in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
if Windows is on the 2nd partition, then root would need to be (hd1,1).

---

