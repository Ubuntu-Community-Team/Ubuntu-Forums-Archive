---
title: "Booting with grub to 2.6.27"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by sjbaugh on 2008-11-02
I have updated from Hary 64 bit to Intrepid 64 bit. As I had edited menu.lst in grub (I have a triple boot system: Windows, Ubuntu and Fedora) I took the default answers to questions about changing menu.lst (ie leave as before), it still boots 2.6.24. During the install I noticed that a new kernel (2.6.27) had been downloaded.

How do I now edit menu.lst to boot the new kernel version?

Thanks,

Steve

---

### Post by caljohnsmith on 2008-11-02
You could add:
```
title		Ubuntu 8.10, [COLOR="Blue"]kernel 2.6.27-7-generic[/COLOR]
root		(hdX,Y)
kernel		/boot/[COLOR="Blue"]vmlinuz-2.6.27-7-generic[/COLOR] root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/[COLOR="Blue"]initrd.img-2.6.27-7-generic[/COLOR]
quiet
```
That should work if you don't have a /boot partition. And of course replace (hdX,Y) with your Ubuntu partition. :)

---

