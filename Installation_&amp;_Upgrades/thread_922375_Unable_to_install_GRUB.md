---
title: "Unable to install GRUB"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by ch_123 on 2008-09-17
I'm attempting to install Ubuntu 64-bit onto my Thinkpad T61. I want to keep the standard MBR for the purposes of maintaining the laptop's recovery partition, so I set the installer to install onto my "/" partition (JFS, approx. 20GB large) However, when the installer gets this far, it gives an error:

```
Executing 'grub-install /dev/sda4' failed.

This is a fatal error.
```

And crashes to desktop. What confuses me alot is that I am able to install GRUB onto the same partition using Arch or OpenSuse. Why can't Ubuntu do it?

---

### Post by caljohnsmith on 2008-09-17
> **ch_123 said:**
> I'm attempting to install Ubuntu 64-bit onto my Thinkpad T61. I want to keep the standard MBR for the purposes of maintaining the laptop's recovery partition, so I set the installer to install onto my "/" partition (JFS, approx. 20GB large) However, when the installer gets this far, it gives an error:

```
Executing 'grub-install /dev/sda4' failed.

This is a fatal error.
```

And crashes to desktop. What confuses me alot is that I am able to install GRUB onto the same partition using Arch or OpenSuse. Why can't Ubuntu do it?
This is just an idea, but there is a known bug during the Ubuntu installation process where it hangs at 94% when it is installing Grub. That might be similar to your problem, and one known way to circumvent it is to format the Ubuntu partition to ext2, install, and then "upgrade" your file system to ext3 afterwards (which is easy). Or another option, albeit a bit more involved, is to install Ubuntu without Grub, and then install Grub afterwards. I would try formatting to ext2 first, and if that doesn't work, install Ubuntu without Grub; then I can help you install Grub if you would like the assistance. Let me know how it goes.

---

### Post by ch_123 on 2008-09-17
Interesting, I was considering that it may not have liked my JFS partition, but then the installers of the aforementioned OSes had no problems. I might try creating a seperate boot partition with EXT2.

---

