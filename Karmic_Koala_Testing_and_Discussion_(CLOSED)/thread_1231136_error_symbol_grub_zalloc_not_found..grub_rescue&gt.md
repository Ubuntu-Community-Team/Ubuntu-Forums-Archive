---
title: "error symbol grub_zalloc not found..grub rescue&gt;"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-08-04
Just rebooted after yesterdays update.

grub rescue>

Help produces no clues

---

### Post by philinux on 2009-08-04
It's been bugged. 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/408699](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/408699)

Tried this at the shell.

set root=(hd1,1)
set prefix=(hd1,1)/boot/grub
insmod /boot/grub/normal.mod > this gives the error re grub_zalloc

---

### Post by philinux on 2009-08-04
Fixed it from livdcd. Got fed up of waiting for a grub shell fix lol.

I'm surprised more haven't chimed in as the update yesterday screws up grub.

---

### Post by taavikko on 2009-08-04
> **philinux said:**
> I'm surprised more haven't chimed in as the update yesterday screws up grub.

Desktop hasn't been restarted for few days,
Laptop few times a day, but haven't been struck by this...

---

### Post by philinux on 2009-08-04
> **taavikko said:**
> Desktop hasn't been restarted for few days,
Laptop few times a day, but haven't been struck by this...

Oh well maybe I is just lucky. :P

---

