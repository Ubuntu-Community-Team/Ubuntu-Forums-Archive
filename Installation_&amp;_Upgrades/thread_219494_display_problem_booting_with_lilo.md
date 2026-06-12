---
title: "display problem booting with lilo"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by roger21 on 2006-07-20
hi,

I installed lilo over grub, it boots fine except when i put a vga=something line, then i got a blank screen

vga=792 worked fine with grub (and it matches my display) i tried vga=791 and vga=normal -> same result

i tried to put my framebuffer driver hard build in the kernel -> same result (i got this message though when i don't put the vga=something line - and so when i can see the boot - : intelfb: Video mode must be programmed at bot time)

if someone has an idea about this issue i'll be glad to try something

thx

---

