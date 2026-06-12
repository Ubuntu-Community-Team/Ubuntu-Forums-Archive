---
title: "Check Disk"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-07-30
I turn my computer on and off allot. I guess after thirty or so turn on/offs, it forces a check of the hard disk. When I was running Ubuntu 7.04, my computer would hang and I could never get it to finish the scan, it would hang. I removed Ubuntu in place for Kubuntu. How do I turn off the forced scan of my hard drive so that regardless of how many time I turn on/off my computer it will never run? It would also help if you could answer this other question. Every time I boot using grub, I need to go to some list by pushing "e" over the script for the kernel and tyoe in vga=792 and noapic, how can I permanently add this? Thank you for all of the help!

---

### Post by merlinus on 2007-07-30
> 
Every time I boot using grub, I need to go to some list by pushing "e" over the script for the kernel and tyoe in vga=792 and noapic, how can I permanently add this?


Add the statements to the end of the kernel line in /boot/grub/menu.lst.

```

gksudo gedit /boot/grub/menu.lst

```-merlin

---

### Post by ErusGuleilmus on 2007-07-30
Since I am using KDE would it be: ```
gksudo kate /boot/grub/menu.lst
``` ??

---

### Post by merlinus on 2007-07-30
```

kdesu kate /boot/grub/menu.lst

```

-merlin

---

### Post by ErusGuleilmus on 2007-07-30
So as for turning off the forced disk check, is that not possible?

---

### Post by merlinus on 2007-07-30
Edit /etc/fstab and change the 1 at the end of / entry to 0.

-merlin

---

