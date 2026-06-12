---
title: "No such partition - Entering rescue mode"
date: 2021-04-18
forum: Installation &amp; Upgrades
---

### Post by leejenon on 2021-04-18
Hi, 

I wanted to reinstall Ubuntu, so I removed the partitions, formatted the O/S drive, plugged my USB ISO image in and booted. I assumed it would boot from the USB drive, but it didn't and said this :-

```
Error: no such partition
Entering rescue mode 
grub rescue>
```

Can I have some help please at starting the reinstallation?

Thanks

Lee

20.04

---

### Post by CelticWarrior on 2021-04-18
How was that USB made exactly?
Have you changed the boot order in BIOS/UEFI?

---

### Post by leejenon on 2021-04-18
Hi Celticwarrior,

I can't remember if I changed the boot order on the initial installation. I haven't changed it on this second install, I'm not sure how to.

I made the bootable USB on my Windows laptop. It was the same USB install I used on the initial install. 

I could make the usb again?

Lee

---

### Post by ubfan1 on 2021-04-18
Is this a UEFI setup?  Did you make USB first in the boot order? Can you select USB as the boot device from the EFI menu (some key at power-up to allow you to choose the boot device/OS)?

---

### Post by leejenon on 2021-04-18
Thank you both for your time, but I have fixed this now. 

It was F2 to get to the Fujitsu BIOS, but I also think the USB ports at the front of Desktop PC are faulty. I changed the boot order to Generic Flash Drive in first priority, and used a port in the rear, and my install is starting now. Wahooo

I don't know how to use UEFI, but I'm learning, this Fujitsu does not implement UEFI specification fully, as I understand.

Lee

---

### Post by yancek on 2021-04-18
> but I also think the USB ports at the front of Desktop PC are faulty 

That may be the case but it is more likely that only some of the USB ports are capable of being used to boot from.  I've seen that on some computers I've used.

---

