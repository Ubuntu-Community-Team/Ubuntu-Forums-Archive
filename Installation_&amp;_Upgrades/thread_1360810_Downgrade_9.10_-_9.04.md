---
title: "Downgrade: 9.10 - 9.04"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by killians31 on 2009-12-21
Hey guys, 

I have decided to downgrade my system from 9.10 to 9.04, as i am having an issue with my sound card not being detected. I have been trying to get this working for some time now, and have finally thrown in the towel!

When i downgrade my partition, would it be advisable to completely wipe that partition clean? Ubuntu is my grub boot loader, which has 3 other operating systems correctly functioning. When i downgrade my system, would the UUID's stay the same? is there any way for my to keep my current grub menu.lst file after the downgrade?

Thanks,
Ben

---

### Post by ajgreeny on 2009-12-21
I think the only way to downgrade from 9.10 to 9.04 is to do a reinstall from scratch, I'm pretty sure there is no reverse of the distro upgrade available.

When doing this your ubuntu partition(s) will have new UUIDs, as you will have to format, so the old menu.lst will be OK except for that problem.  To be honest, though, I would let the new install make a new menu.lst, as ubuntu, unlike most other linux distros, is excellent at picking up and adding all other OSs to the grub menu.  Even if it does not do so, it should be very easy to add anything missing afterwards.

---

### Post by me? on 2010-03-29
yess there is no way

---

