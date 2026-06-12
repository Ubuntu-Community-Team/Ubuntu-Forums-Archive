---
title: "grub no menu"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by vegetto on 2005-04-13
I installed ubuntu from knoppix live cd and it's working fine except that the bootloader grub has no menu even though i have a menu.1st in /boot/grub folder. i tried to install lilo but in the last step says it is unable to install in mbr. what do i do? am i missing something.

---

### Post by erkki70 on 2005-04-13
Hi,
Could you post your menu.lst file?
It might contain precious info in order to help.

Cheers,
Erkki

---

### Post by vegetto on 2005-04-13
sure, /boot/grub/menu.1st. one more thing, this maybe dumb but my grub.conf and menu.1st are the same. how come?
> 

 color black/cyan yellow/cyan
        timeout=5
        default=0

title=Ubuntu
  root (hd0,2)
  kernel /vmlinuz root=/dev/hda3
  initrd /initrd.img

title=Windows
  root (hd0,0)
  makeactive
  chainloader +1

title=Memtest86
  root (hd0,2)
  kernel /boot/memtest86+.bin




---

### Post by erkki70 on 2005-04-13
Hi,
Is this all you have in the file?
Nothing before that, more text?

Just in case there is more text before you have to comment the line  ```
hiddenmenu
``` to  ```
#hiddenmenu
```

Then run  ```
sudo update-grub
``` so it makes the changes active.

Hope this helps.
Cheers,
Erkki

---

### Post by vegetto on 2005-04-13
No, that's the full file.

---

### Post by vegetto on 2005-04-13
i am really dumb i put menu.1st instead of menu.lst. everything fine now.

---

