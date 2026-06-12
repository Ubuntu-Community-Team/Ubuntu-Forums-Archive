---
title: "Can't install or uninstall software"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by jb1972 on 2008-05-21
Using ubuntu 8.04 hardy. Yesterday i was installing some software from add/remove when there was a power cut. Obviously my computer instantly shut off, but since then i cannot add or remove any programs. I get this message instead... 



[IMG]http://i85.photobucket.com/albums/k58/speedy1_photos/Screenshot-synaptic.jpg[/IMG]



Also, i use firefox 2. but since the power cut only version 3 will startup, even when using the icon for 2.

Help!

---

### Post by forestpixie on 2008-05-21
Try to run the command it gives - you need to add root rights with sudo

```
sudo dpkg --configure -a
```

---

### Post by clb137 on 2008-05-21
> **jb1972 said:**
> Using ubuntu 8.04 hardy. Yesterday i was installing some software from add/remove when there was a power cut. Obviously my computer instantly shut off, but since then i cannot add or remove any programs. I get this message instead... 



[IMG]http://i85.photobucket.com/albums/k58/speedy1_photos/Screenshot-synaptic.jpg[/IMG]



Also, i use firefox 2. but since the power cut only version 3 will startup, even when using the icon for 2.

Help!


in a terminal window you must the following: sudo dpkg --configure -a you will be asked for your password,

have a go, good luck

clint

---

### Post by jb1972 on 2008-05-21
That sorted it. Nice one cheers :):)

---

