---
title: "Upgraded from 7.10 to 8.04 now USB storage will not mount"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by jbeiter on 2008-11-19
I recently went through the update from 7.10 and 8.04 and now my usb flash drives and iPod Nano will not automount.

I tried booting with them plugged in, gtkpod can't find it.

When I plug the iPod in, The iPod will sometimes say "connected" then immediately say "disconnect when ready" Most of the time the screen just lights up with no connection. The system is not mounting it.

If I knew what device file the ipod should be using on the system, I could try manually mounting it.

Can anyone advise me what to try or how to go about determining what the device file *should* be on Ubuntu 8.04?

This all worked fine under 7.10. I dread what I may have to go through to get Amarok working again..

---

### Post by jbeiter on 2008-11-19
through just unplugging it and plugging the iPod on again, it mounted automatically one time on:

/dev/sdd1              3798592   3410240    388352  90% /media/IPOD

When I tried to transfer songs to it, it dismounted and will not mount again. I tried manually mounting /dev/sdd1 on /media/IPOD and it says /dev/sdd1 does not exist.

Any help? Is 8.xx just flakey and I should consider reloading 7.10?

Is there something I need to tweak or add or update for the USB support to work properly?

---

### Post by jbeiter on 2008-11-20
bump... can anyone throw me a bone here?

---

