---
title: "Grub menu never appears."
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by EtanSivad on 2007-06-14
Anyone have any ideas why my grub menu never appears?  I get the command line and I can type the keneral/initrd commands and get into Ubuntu.

My /boot/grub/Menu.lst  is as follows:

> Timeout 30
default 0

#Ubuntu with with Splash
Title Ubuntu with splash
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb1 ro splash
initrd /boot/initrd.img-2.6.20-15-generic
boot

#Ubuntu with text
Title Ubuntu USB no splash
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb1 ro 
initrd /boot/initrd.img-2.6.20-15-generic
boot



Thanks,
-Etan

---

### Post by bapoumba on 2007-06-14
hello,
You did paste only the relevant info, didn't you?
Can you see it pop up if you hit the <escape> key?
If so, comment the following line:
```
hiddenmenu
```

---

### Post by EtanSivad on 2007-06-14
That's my full menu.lst.  I followed some examples online to write it.  (The ubuntu install didn't like the drive I was installing to and it crashed during the grub install.)

Anyway, I hit escape but the menu never appears and there's nothing entered for "hiddenmenu"

Maybe grub just doesn't like the setup?  I've got Ubuntu installed to a usb drive that I boot my laptop from and it never touches the HD (Hence the /dev/sdb1)


-Etan

---

### Post by bapoumba on 2007-06-15
> **EtanSivad said:**
> That's my full menu.lst.  I followed some examples online to write it.  (The ubuntu install didn't like the drive I was installing to and it crashed during the grub install.)

Anyway, I hit escape but the menu never appears and there's nothing entered for "hiddenmenu"

Maybe grub just doesn't like the setup?  I've got Ubuntu installed to a usb drive that I boot my laptop from and it never touches the HD (Hence the /dev/sdb1)


-Etan

*BUMP* for  EtanSivad. Not sure I can help here.

---

