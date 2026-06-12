---
title: "my computer boots to XP no grub screen"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by digitalslavery on 2008-02-13
I see alot of issues with this one but I have not been able to figure it out on my own, doh! I have XP set up on a 3 drive raid 1 configuration. In XP I set up 2 partitions, C and D, C is the primary and is where XP is installed, D was just the left over space, which is where I installed 7.10 to. During the install process I did the manual partition and resized the D drive, then added 2 partitions for the ext3 and the swap. The install seemed to go just fine but when I restart my computer the grub loader does not show up and my computer just boots into XP.

I tried using sudo grub-install hd0 but get this error: Could not find device for /boot: Not found or not a block device.

what do I need to do to resolve this?

Thanks!

---

### Post by digitalslavery on 2008-02-14
Well turns out my drives were mirroring not in a raid configuration, once I deleted the raid array and changed the bios to see the drives individually on reboot grub popped up and let me boot into either xp or ubuntu, I chose ubuntu of course!

note to self: disable software raid before trying to install linux.

---

