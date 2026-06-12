---
title: "Unable to use gfxpayload= instead of vga="
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jamadagni on 2009-08-24
Hello.

I am using Koala with latest updates upto 2009-08-24 and grub version is 1.96+20090725-1ubuntu2:

When I boot into Jaunty using it it tells me that vga= is deprecated and asks me to use "set gfxpayload=1024x768x24;1024x768" (without the quotes of course) before the linux line.

However, if I add (via 40_custom) to my grub.cfg the line "set gfxpayload=1024x768x24;1024x768" before the linux line, I get: "1024x768: Unrecognized command". If I remove the ";1024x768", I get a black screen upon booting into Jaunty and nothing is visible at all.

Please help.

P.S: I am using GRUB Legacy of Jaunty on the MBR and GRUB 2 of Koala is installed on to the Koala partition and I am chainloading from GRUB Legacy to GRUB 2.

---

### Post by dino99 on 2009-08-24
hi,
i'm using gfxpayload=true , and it work fine for me.

You said: grub legacy is your main loader on Jaunty & then chain grub2 on karmic: grub2 work on jaunty too

You have to use os-prober to find other Os

---

### Post by vishalrao on 2009-08-24
i read somewhere you go to grub2 prompt and type "vbeinfo" (after doing "insmod vbe" i believe) to get a list of supported modes then pick the one that suits you the most...

---

