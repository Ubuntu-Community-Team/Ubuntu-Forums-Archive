---
title: "every upgrade systematically breaks my grub"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Rubbing Alcohol on 2007-02-13
This problem started happening after I upgraded to Edgy. Ever since then, any kernel updates via apt-get or synaptic (in fact, just about any update that needs a reboot) breaks my grub.lst.

Im dual-booting with XP and this is what it should look like:
```

root (hd0,1)
kernel /vmlinuz root=/dev/hda2
 initrd /boot/initrd.img-2.6.17...
boot

```
 but every update changes it back to: 
```

root (hd0,2)
kernel /vmlinuz root=/dev/hda3
 initrd /boot/initrd.img-2.6.17...
boot

```

Any thoughts on what could be causing this?

Thanks

---

### Post by GoingDown on 2007-02-13
Take a look of "# groot=(hd0,2)" line on /boot/grub/menu.lst file, and change it to "# groot=(hd0,1)".

---

