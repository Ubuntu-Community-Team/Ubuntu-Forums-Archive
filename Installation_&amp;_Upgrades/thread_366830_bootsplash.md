---
title: "bootsplash"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-02-21
Hey
I complied a new kernel today and now the bootsplash doesnt work.
How can i get it back or install a new one?

Thanks

---

### Post by logos34 on 2007-02-21
Post your grub config file:
> cat /boot/grub/menu.lst

---

### Post by dmsn on 2007-02-21
title           Ubuntu, kernel 2.6.20-dmsn
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20 root=/dev/sda2 ro quiet splash
quiet
savedefault
boot

#title          Ubuntu, kernel 2.6.17-11-generic
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
#initrd         /boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault
#boot

---

### Post by logos34 on 2007-02-21
> title Ubuntu, kernel 2.6.20-dmsn
root (hd0,1)
kernel /boot/vmlinuz-2.6.20 root=/dev/sda2 ro quiet splash
**quiet**
savedefault
boot

take out that second quiet.  see if that does it

---

### Post by logos34 on 2007-02-21
or is that the tail end of a missing 'initrd' line for the kernel image? 

initrd  /boot/intird.img-2.6.20-dmsn 
quiet                                                (?)

---

### Post by dmsn on 2007-02-21
There is no such file in /boot

initrd /boot/intird.img-2.6.20-dmsn

---

