---
title: "Need advice in removing old kernel"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by bonifacio on 2005-03-17
Here's what I'm about todo:
[list]
[*]Edit my grub menu list and remove the old kernel
[*]Remove the files referenced by that old kernel, mostly in /boot/
[*](... anything else I need todo? ...)
[/list]

---

### Post by sunscape on 2005-03-17
LIKE, use synaptics to remove the old kernel. But keep a working version around because you never know...

---

### Post by bonifacio on 2005-03-17
Will synaptic update Grub's list?

---

### Post by mips on 2005-03-17
Yes, it did for me.

cheers
mips

---

### Post by adun on 2005-03-17
You find the grub menu in /boot/grub/menu.lst

---

### Post by mips on 2005-03-18
Why would you want to edit the grub menu if you can do it from synaptic ???


cheers
mips

---

### Post by bonifacio on 2005-03-18
It's nice to know how to do it without the aid of a GUI tool.

And yes synaptic handles the removal of the old kernel so is the entry in grub.  I suppose apt's command could have done the same thing for those who like it on the command line.

---

