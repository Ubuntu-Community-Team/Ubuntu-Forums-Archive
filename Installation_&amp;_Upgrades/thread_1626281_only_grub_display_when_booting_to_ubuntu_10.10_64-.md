---
title: "only grub display when booting to ubuntu 10.10 64-bit"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by lordpaladin on 2010-11-20
hello everyone...

im here again to ask a little help
im dual booting my desktop pc with a windows xp 32 bit and an ubuntu 10.10 64-bit
i have already installed ubuntu 10.10 with no problems at all but when im selecting ubuntu, all i see is grub. i dont do to the ubuntu os.

heres how i installed my ubuntu:
i manually made a partition of ubuntu using the live cd
format is ext4
mount is /
40b hard disk space
[CENTER]installed at the beginning
[/CENTER]
set as primary
then on the place where to install the boot loader, i placed it on the same partition where i will install ubuntu

did i made a wrong procedure?

---

### Post by Rubi1200 on 2010-11-20
> **lordpaladin said:**
> then on the place where to install the boot loader, i placed it on the same partition where i will install ubuntu

did i made a wrong procedure?
Unfortunately, yes.

Fortunately, the fix is usually quite simple.

The bootloader needs to be installed to the MBR of the main drive (usually sda).

However, to make sure there are no other issues involved, please click on the boot info script link at the bottom of my post.

Follow the instructions there and post the results back here so we can take a look.

Thanks.

---

### Post by lordpaladin on 2010-11-20
thanks for the advice...
did a complete re-install and now its working....
thanks very much!

---

### Post by Rubi1200 on 2010-11-20
Okay, I am glad it is all sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

