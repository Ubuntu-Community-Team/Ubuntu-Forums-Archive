---
title: "How to remove WUBI install"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-03-02
I have two computers. One has to stay Windows the other is Ubuntu. I had installed Ubuntu as a wubi install on that windows machine. I uninstalled via add/remove programs but the loader is still there. How do I get rid of that? It's not a big issue cause I just set Windows as the first boot wh\ith a 3 second time so it loads right up. Just want to know how.
Thanks

---

### Post by darkod on 2010-03-02
If using XP just open C:\boot.ini and delete the ubuntu line. Note that it's probably a hidden file.

For vista/7 I believe you need to use the command

bcdedit.exe xxxxxxx

but I don't know the exact syntax. Try google for how to use it. MS changed the way of editing the boot information from vista. And that file bcdedit.exe should be in C:\Boot folder, also hidden.

---

### Post by Silvertones on 2010-03-02
Thanks that did it.

---

