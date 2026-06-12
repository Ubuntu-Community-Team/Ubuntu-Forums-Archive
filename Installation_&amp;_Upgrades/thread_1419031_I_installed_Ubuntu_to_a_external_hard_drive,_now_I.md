---
title: "I installed Ubuntu to a external hard drive, now I can't start windows without it."
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by Garryonapc on 2010-03-01
The BIOS seems to be defaulting to the new Grub start-up which is now stored on the USB external HD. How do I get the normal windows start-up to run automatic?
I have gone through the BIOS and told it to boot from internal HD but to no avail. I haven't done anything to the Grub program yet because I don't really know what I'm doing with it.

---

### Post by darkod on 2010-03-01
BIOS will always look first where you tell it to. But grub2 ended up on your internal disk, you need to check that during the ubuntu install to make sure. Don't just assume.

Read here the first posts up to #5, it's exactly the same situation. The fix is easy.
[http://ubuntuforums.org/showthread.php?t=1418411](http://ubuntuforums.org/showthread.php?t=1418411)

---

