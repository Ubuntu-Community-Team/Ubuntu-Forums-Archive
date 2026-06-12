---
title: "Grub and Xen"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Ekman on 2007-05-21
I've installed Xen under Ubuntu Feisty and it works great.
The only problem is when booting the DomU - another Feisty install, not debootstrapped but installed with PAE enabled.

When i fire up a vnc client to the newly started DomU, I always see the grub menu, halted at "The highlighted entry will be booted automatically in 3 seconds."
If i press enter it loads the highlighted kernel.

I have tried changing in menu.lst to no timeout but it is the same.. It sits there and waits there for me too press enter, and then it works ok.

Strange? How can I make it start like it should?

---

