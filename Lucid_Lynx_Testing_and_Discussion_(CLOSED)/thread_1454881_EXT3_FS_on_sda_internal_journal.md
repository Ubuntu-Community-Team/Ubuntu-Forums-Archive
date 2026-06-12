---
title: "EXT3 FS on sda internal journal"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clafa on 2010-04-15
upgraded to beta 2 from intrepid and restarted. I get "EXT3 FS on sda internal journal" and then it stops... I've tried removing quiet splash in grub but same result. I've also tried all_generic_ide but without luck... Anyone know why? some kind of SATA problem with this kernel version?

I can boot the live cd and check my sda drives but it all comes out clean... what the heck is causing this?

---

### Post by Malawi on 2010-04-15
I have the same problem, except I upgraded from Koala.
Anyone?
Thanks

---

### Post by clafa on 2010-04-18
no one seen this before?

---

### Post by clafa on 2010-04-19
There seems to be some kind of problems with the UUID's in FSTAB. When I replaced them with labels instead eg. /dev/sda2 it booted!!:popcorn:

---

### Post by Malawi on 2010-04-21
what did you changed exactly?

I have:
```
uuid xxxxxx-xxxxx...
kernel /boot/vmlinuz-2.6... root=UUID=xxxx-xxxx...
initrd /boot/initrd.img-2.6...
quiet
```

Did you changed the 1st line? And how?
In the 2nd line, I tried root=/dev/sdax. Is it correct?

How do you know the number in sdax?

Thanks

---

### Post by clafa on 2010-04-23
I didnt change anything in grub,,, but in etc/fstab i replaced all uuid's with labels instead.

# Entry for /dev/sda2 :
/dev/sda2 / ext3 relatime,errors=remount-ro 0 1
#UUID=77f52ff6-79a6-468c-9b3d-70456ed38ac0

---

### Post by Malawi on 2010-04-23
Thanks clafa,

But how did you changed your fstab if your linux doesn't work?
I tried with a live-cd and I have the same problem...

---

### Post by clafa on 2010-04-23
> **Malawi said:**
> Thanks clafa,

But how did you changed your fstab if your linux doesn't work?
I tried with a live-cd and I have the same problem...

You get the same result booting from a live cd? have u tried the alternative live cd? I had no problem booting from a live cd and then i could mount the volume and change fstab.

---

