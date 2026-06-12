---
title: "-3 Kernel Changes"
date: 2008-07-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-05
So the new -3 kernel has fixed the system clock boot error for me.

Though a new error - I cant run a higher grub vga resolution than default - if I try to I get a blank screen until the GDM inits up.

---

### Post by ShirishAg75 on 2008-07-05
I love the changelog given, I would be trying to know all the updates it has done since the last version.

---

### Post by autocrosser on 2008-07-05
I don't think that is related to grub--sounds more like a Usplash problem--If it's after you select a kernel in grub--that is when grub hands off to Usplash--Try changing you /etc/usplash.conf & see what happens.....

---

### Post by Nullack on 2008-07-05
Im not using usplash

---

### Post by Amaranth on 2008-07-06
This was broken in hardy as well. You don't get any display on boot if you have a vga= option in your boot line.

---

### Post by stari4ek on 2008-07-07
> **Amaranth said:**
> This was broken in hardy as well. You don't get any display on boot if you have a vga= option in your boot line.

I'm not sure about current state, but 2 weeks ago it works well for me. I just add fbcon, vesafb to initram's modules.

As I see 2.6.26-3 switched to uvesafb, which doesn't work.

Thread about this bug (i posted temporary walkaround there):
[http://ubuntuforums.org/showthread.php?p=5336540](http://ubuntuforums.org/showthread.php?p=5336540)

The problem with uvesafb could be:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/189621](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/189621)

I posted bug to launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

---

### Post by Nullack on 2008-07-10
Good stuff - would be great to see this bug with the vesa framebuffer fixed in time for alpha 2

---

