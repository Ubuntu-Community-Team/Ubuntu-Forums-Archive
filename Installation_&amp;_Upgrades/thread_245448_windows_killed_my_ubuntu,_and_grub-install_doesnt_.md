---
title: "windows killed my ubuntu, and grub-install doesnt work!"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by sapo on 2006-08-27
Hi guys, i did a bad thing here.. installed windows :(

Now my grub is gone, i did it several times before, but in breezy i just had to put the cd in the drive... enter in rescue mode and then type grub-install /dev/sda (i have a sata hd)

So i tried with the dapper live cd, mounted the root partition and used chroot.. then when i type grub-install /dev/sda, it cant find /dev/sda

After that i tried the breezy cd, and when i do it i got this messagem:

/dev/sda not supported by BIOS driver (or something like it)


Please, could you guys give me some idea how can i have my grub back? :(

Thanx in advance

---

### Post by confused57 on 2006-08-27
Maybe you can use the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by sapo on 2006-08-27
> **confused57 said:**
> Maybe you can use the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
that solved it.. i used the grub shell and installed it again using chroot!

thanx a lot!

---

