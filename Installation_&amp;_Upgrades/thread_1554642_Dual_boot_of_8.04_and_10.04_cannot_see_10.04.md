---
title: "Dual boot of 8.04 and 10.04 cannot see 10.04"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-08-17
I have a dual boot PC  where I started with 10.04 and later installed 8.04.4 for various reasons. Because 10.04 is ext4, I guess that 8.04.4 cannot see it so that the recently installed 8.04.4 grub does not include 10.04, so when booting normally now, I cannot see nor start 10.04.

I guess I have to somehow run 10.04 and ask it to run or update its grub?

Or can I reset grub in 10.04 to take over when I boot up?

tia

---

### Post by candtalan on 2010-08-17
done it.
I acted as if I had installed Windows after first installing Ubuntu and followed the reinstall of grub2 using a 10.04 live CD

Reinstalling from LiveCD
[...]
SIMPLEST - Copy GRUB 2 Files from the LiveCD
[...]

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

