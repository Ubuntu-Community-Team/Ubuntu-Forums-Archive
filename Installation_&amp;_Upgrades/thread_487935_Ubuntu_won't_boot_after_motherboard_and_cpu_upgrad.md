---
title: "Ubuntu won't boot after motherboard and cpu upgrade"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by forchessonly on 2007-06-29
I just upgraded my mother board and cpu from an Asus A7V8X w/ AthlonXP2400 to a PCChips P23g w/ Intel Core 2 Duo. 

GRUB can successfully start loading Ubuntu, it finds the kernel, extracts it, and the the Ubuntu loading screen pops up. When Ubuntu tries to load the root partition it just stalls and says waiting for root partition.

Do I have to reinstall Ubuntu when I replace my motherboard and cpu?

Thanks.

---

### Post by awaldram on 2007-06-29
no but you'll porbably need to re-install if you change your south Bridge / IDE controller.

Which you have done going from amd to intel..

it is fixable without re-install ,but will be quite involved basicaly

find out what module you require to support your hard disk
boot rescue disk
swivel root
rebuild initramfs with module required
reboot.

---

### Post by wpshooter on 2007-06-29
> **forchessonly said:**
> I just upgraded my mother board and cpu from an Asus A7V8X w/ AthlonXP2400 to a PCChips P23g w/ Intel Core 2 Duo. 

GRUB can successfully start loading Ubuntu, it finds the kernel, extracts it, and the the Ubuntu loading screen pops up. When Ubuntu tries to load the root partition it just stalls and says waiting for root partition.

Do I have to reinstall Ubuntu when I replace my motherboard and cpu?

Thanks.

Unless you want to re-invent the wheel, in a word YES.

---

### Post by Pumalite on 2007-06-29
I agree. There is no way that system is going to work with a new chipset.

---

