---
title: "Unable to Boot"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Vaderdarth211 on 2007-08-21
I used the text based installer to install. it says it has finished but i can't boot Ubuntu.  Please help

---

### Post by heimo on 2007-08-21
> **Vaderdarth211 said:**
> I used the text based installer to install. it says it has finished but i can't boot Ubuntu.  Please help

You need to give more details before anyone can try to help you.

---

### Post by Vaderdarth211 on 2007-08-21
I used the text based installer because the bootable cd linux was tooslow for me. It said it completed installation and then tried to reboot. The system kept rebooting nonstop and wouldn't boot ubuntu at all.it said error loading Grub

---

### Post by Pumalite on 2007-08-21
Post your specs.

---

### Post by Vaderdarth211 on 2007-08-21
AMD athlon 64 755 mgh
384 mb ram
2 mb videocard (PCI)
2 60 gb Maxtor IDE hard Disk

---

### Post by Pumalite on 2007-08-21
Get a Knoppix Live CD and see if you can boot it. It will mount your filesystem and you can then post: sudo fdisk -l (small L) and 'cat /boot/grub/menu.list' from the Terminal ( if they exist)

---

### Post by Vaderdarth211 on 2007-08-21
where and how

---

### Post by Pumalite on 2007-08-21
[http://www.knoppix.org/](http://www.knoppix.org/)
How? Read Documentation.

---

### Post by Vaderdarth211 on 2007-08-21
thanks

---

