---
title: "Out of ideas..."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by fbaerkir on 2008-04-27
I've been trying for weeks now to install Ubuntu, with no luck, so I'm hoping maybe I'm just overlooking something simple and someone can steer me right.
I run Windows on a RAID 5. So first I followed some tutorials  on running dmraid to place Ubuntu on a partition of that RAID. No dice - dmraid doesn't see the array.
So I added another hard drive. I tried putting Ubuntu on that, but it altered the Windows MBR. Fixing that meant I couldn't boot Linux.
I tried setting the install options of Ubuntu to leave the other drives alone and install GRUB on the same HD. That left Linux unbootable.
I tried that same method with the alternate install CD, with the same result.
I tried setting the options to install GRUB on a floppy. GRUB hung up on stage 1.5, though.
I tried editing the floppy GRUB per another thread on this forum, changing the root locations. That still didn't work; it came back with "hard drive error."
I tried putting GRUB on the HD, and editing it on that. Same result.

So, I think I've been pretty stubborn trying to get Linux installed. If someone were to install Ubuntu on a separate HD that coexists with Windows on a separate RAID, how should they do it?

---

### Post by fbaerkir on 2008-04-28
So, I'm guessing this isn't really possible?

---

