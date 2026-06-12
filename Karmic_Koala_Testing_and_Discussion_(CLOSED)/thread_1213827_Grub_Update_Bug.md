---
title: "Grub Update Bug"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hgergo on 2009-07-15
After updating to the 2.6.31.3 kernel grub is not updating and at restart the new kernel is not showing .
How can i update grub or i most edit it maualy?

---

### Post by MacUntu on 2009-07-15
sudo update-grub2

---

### Post by infiner on 2009-07-15
As of the date of this post, still not working...

```
# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.30-8-generic
Found initrd image: /boot/initrd.img-2.6.30-8-generic
Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by infiner on 2009-07-15
Oh yeah version might help: 

```
$ uname -a
Linux mycomputer 2.6.30-8-generic #9-Ubuntu SMP Wed Jun 3 15:23:55 UTC 2009 i686 GNU/Linux
```

---

### Post by infiner on 2009-07-15
This was fixed after updating all in Synaptic, yay!

```
# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-3-generic
Found initrd image: /boot/initrd.img-2.6.31-3-generic
Found linux image: /boot/vmlinuz-2.6.30-8-generic
Found initrd image: /boot/initrd.img-2.6.30-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

