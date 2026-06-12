---
title: "How to change boot time resolution?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by jpnurmi on 2006-06-04
Hello,

I have a fresh and clean installation of Kubuntu Dapper. I encountered some problems during my live cd installation attempts so I switched to the alternate cd and then everything worked flawlessly.

Without getting bogged down into details, (in addition to the installer crash) one of the problems with the live cd was that my monitor (LG L1915S) was somehow incompatible with the default VGA resolution. My monitor kept saying "Out of range 36.2 kHz / 81Hz" until I realized that the resolution can be changed..

Anyway, I eventually managed to install Dapper successfully by using the alternate cd's text mode installation. Now the problem is, during the boot, my monitor still keeps saying the same "Out of range 36.2 kHz / 81Hz", but only until X starts. Afterwards everything is fine.

So my question is; is there any way to change the boot up resolution like in the live cd?

- JP

---

### Post by adament on 2006-06-04
You have to change your boot options in /boot/grub/menu.lst. Change the vga= mode to one of those listed below. 
I managed to find the list below of different vga= modes.
res/col | 640x480  800x600  1024x768 1280x1024
--------+-------------------------------------
256     |  0x301    0x303    0x305    0x307
32K     |  0x310    0x313    0x316    0x319
64K     |  0x311    0x314    0x317    0x31A
16M     |  0x312    0x315    0x318    0x31B

---

### Post by jpnurmi on 2006-06-05
Perfect! That solved the problem. Thanks a lot adament! ;)

---

