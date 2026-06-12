---
title: "How do I safely remove/repair a failed upgrade?"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by mooz123 on 2012-02-25
I did a partial upgrade to kernel 3.0.0.16. Afterwards the x server was not working, it seemed. I got a terminal prompt, could log in and the command xstart was not recognized. 3.0.0.15 is still working fine.

Could somebody please help me, what is the best way to repair this?

HP desktop, Ubuntu 11.10, Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2

---

### Post by darkod on 2012-02-25
Not sure if a repair is better and how to do it, but you can remove it with:
sudo apt-get remove --purge linux-image-3.0.0-16-generic

After that run:
sudo update-grub

to modify the boot menu.

You can probably install -16 later again.

---

### Post by mooz123 on 2012-02-25
That solved it, thank you Darko.
Ubuntu magic: posted, answered, implemented and tested in 12 minutes!:)

---

