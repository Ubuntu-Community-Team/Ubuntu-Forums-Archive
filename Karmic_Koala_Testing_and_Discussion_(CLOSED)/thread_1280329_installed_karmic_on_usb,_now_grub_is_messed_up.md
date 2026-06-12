---
title: "installed karmic on usb, now grub is messed up"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sjpn on 2009-10-01
Hi,
I recently installed karmic onto a usb and ran my laptop off of the karmic usb drive. Now when I try to boot my regular laptop (jaunty) i just get a prompt like

GRUB loading.
error: no such disk
grub rescue>

Any ideas how I can fix this?
Thanks

---

### Post by vishy1618 on 2009-10-01
Damn, man, I have the same ridiculous problem. Seems like GRUB 2 is seriously messed up. Please anyone, reply...

---

### Post by sjpn on 2009-10-01
i think grub is trying to look for the usb drive when it starts up. i can boot normally if i press <esc> while grub is loading and select my kernel on my /dev/sda1 partition. i think if i modify something in /boot/grub - like remove any reference to /dev/sdb then it might fix it.

---

### Post by sjpn on 2009-10-01
I tried this:

remove reference to /dev/sdb from /boot/grub/device.map
run grub-install /dev/sda1
restart

but it still doesn't work. i better not lose my usb drive!

---

### Post by sjpn on 2009-10-02
ok. it's working now
i just had to run

grub-install /dev/sda

not the partition sda1
and it works fine now.

---

