---
title: "GRUB&quot; Dead Slow"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2009-12-07
Hi,

I have a dell dimension with 2 hard drives and a USB hard drive called "My Book".

When the system boots, grub2 hangs for a full 15 seconds saying Grub Loading.  This is much slower than grub 1.  Also:

When I do a update-grub2 it hangs for 1 min 45 sec after the memory test and then reports:```

ls: cannot access /media/My: No such file or directory 
```

It is looking for "My" rather than "My Book"

It does this even if the USB drive is unplugged.  So how does it know it is there?

Any ideas how to get grub to ignore the usb drive and speed boot up time please?

---

