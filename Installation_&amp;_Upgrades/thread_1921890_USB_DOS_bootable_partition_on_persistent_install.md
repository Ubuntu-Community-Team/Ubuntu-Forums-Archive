---
title: "USB DOS bootable partition on persistent install"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by MkJackson on 2012-02-07
Hey folks,
This persistent install USB kit has proven invaluable. I currently have sda1 as a 16 general purpose USB drive and the second partition as my persistent Linux install. 

However, I was looking to add ms-dos to the first partition which I could load into via grub. However, at the moment all I get is a "boot error" screen. 

Here's what I've added to the /etc/grub.d/ directory:
/etc/grub.d/31_dos
#!/bin/sh
exec tail -n +3 $0

menuentry "DOS" {
    insmod chain
    insmod fat
    set root=(hd0,1)
    chainloader +1
}

Thoughts?

---

