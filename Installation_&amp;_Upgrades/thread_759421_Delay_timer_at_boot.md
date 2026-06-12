---
title: "Delay timer at boot"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Wheelz77 on 2008-04-19
I have a dual boot installation and I'm getting tired of the 10sec delay timer after the Ubuntu selection has been made.
Could some kind person please tell which file I can edit (and where to find it) and which application I need to use to edit it?
I'm a noob to Linux.

Cheers.

---

### Post by Rocket2DMn on 2008-04-19
You would run
```
gksudo gedit /boot/grub/menu.lst
```
Near the top of the file there is "timeout" and a value (10) which you can change.  Maybe drop it down to 5 seconds or so, there may be times when you actually need to select other entries, like the recovery mode kernel.

---

### Post by Wheelz77 on 2008-04-19
Thanks Rocket2Dman for the speedy reply.
Just edited it and tried it. Sweet as!!
Thanks again.

---

