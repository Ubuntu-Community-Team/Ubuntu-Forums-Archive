---
title: "Install inside Windows failed"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by TehNrd on 2008-05-17
I tried the new feature that lets you install ubuntu inside windows but it appears this has failed. 

The windows portion of the install works fine.

It then reboots and I select Ubuntu from the OS list. It loads up fine and does some additional installation 

After this it reboots one more time. At the OS selection screen I select Ubuntu and I get this error:

```

File  System is NTSF, partition type 0x7

kernel /boot/vmlinux-2.6.24-16-gen root=wiD4ACC73CACC711C2 lopp=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continute...

```

Pressing any key takes me to the GRUB loader and anything I select fails. I can then restart, select windows at the windows boot loader and Windows will load fine.

C: drive is the drive that has windows on it but for the Ubuntu installation I installed it to a logical drive F: which is basically just an extra drive for storage. Would this cause the issue. Does the Ubuntu installation need to be on the same drive as Windows?

---

### Post by Pumalite on 2008-05-17
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

