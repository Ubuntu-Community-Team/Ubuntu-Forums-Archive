---
title: "Add Karmic to Jaunty boot in Grub2 config"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-26
I have Jaunty installed as my primary OS, and would like Karmic installed for a dual boot system. I want Karmic installed for testing, and when I'm happy with it, I will upgrade Jaunty and replace Karmic with the next alpha release.

But, I would like grub2 installed for Jaunty (which I've done successfully) and chainload into Karmic (seeing as the kernel updates so quickly in alpha). One idea was to add:
```
menuentry "Ubuntu Karmic Koala alpha" {
linux /vmlinuz root=(hd0,4) so quiet splash
initrd /initrd.img
}
```
... but I get a kernel panic.

Other ideas please?

---

### Post by phenest on 2009-07-27
```
menuentry "Ubuntu Karmic Koala" {
set root=(hd1,2)
linux /vmlinuz root=/dev/sdb2
initrd /initrd.img
}
```
...will boot from a 2nd hard drive. That's great, but I want to boot Karmic from another partition on the same drive. I'm either getting a kernel panic or, at best, I end up with:
```
(initrmfs) _
```

---

### Post by phenest on 2009-07-27
```
menuentry "Ubuntu Karmic Koala" {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 so quiet splash
initrd /initrd.img
}
```

...et voila!

---

