---
title: "[SOLVED] boot priority"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by glennnf on 2008-06-26
Hi guys,this is my first thread so be patient.I have changed the default value in my menu.lst(Ubuntu 8.04) so as Windows will be first boot choice,but i cant save the changes, iam getting a "dont have permission" message,any suggestions. Thanks.

---

### Post by Pumalite on 2008-06-26
To edit menu.lst:
gksudo gedit /boot/grub/menu.lst
Make the changes
Now: File>Save.

---

### Post by glennnf on 2008-06-26
Thanks Pumalite,i think i was trying to change the default value through the file browser rather than  a command line.anyway it worked,thanks again.

---

### Post by Pumalite on 2008-06-27
You are welcome. Good luck.

---

