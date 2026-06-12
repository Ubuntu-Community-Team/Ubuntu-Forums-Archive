---
title: "ubuntu 10.04, legacy grub 0.97, and vga= grub option"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by igtrnt on 2010-06-01
Hello,

After reading multiple posts at various forums, I still cannot figure out how to make vga= option work with ubuntu 10.04 and legacy grub, or what is the alternative for that option when not using grub 2?

------------------------
Dell XPS M1530, Ubuntu Desktop 10.04 64bit

---

### Post by darkod on 2010-06-01
The number you use depends on the resolution you want to use. I think the usually used is vga=771.

You just add it at the end of the kernel line I believe.

---

### Post by igtrnt on 2010-06-01
the problem is that apparently 10.04 does not recognize this option or has a bug.
If I add vga=0x365 (1440x900 on my Dell XPS M1530) then, instead of seeing text, I just see noise in the upper part of the screen.

vga=0x365 worked fine with Ubuntu 9.04, which I had installed previously

---

