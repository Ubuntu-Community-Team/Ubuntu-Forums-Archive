---
title: "Can I move Grub?"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by loumsmith on 2008-05-17
When I installed Ubuntu in 2006, Ubuntu was installed on an external USB drive.  XP was already installed on the C: drive.  The boot loader (GRUB) looks for the USB drive on boot.  Therefore, I can't boot the native windows installation without the USB drive plugged in.  Is there a way to modify things so I can still boot into XP if I forget the external drive?

Thanks again,

Louis

---

### Post by meierfra. on 2008-05-17
I wrote a howto for this situation Click on "Dual" in my signature. If you are using "ubuntu 8.04" you also need to look at the last post in that thread. If you need help  additional help please post the output of


```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

( both "l" are lowercase L)

---

### Post by loumsmith on 2008-05-18
Thanks, I will give it a try.
Louis

---

