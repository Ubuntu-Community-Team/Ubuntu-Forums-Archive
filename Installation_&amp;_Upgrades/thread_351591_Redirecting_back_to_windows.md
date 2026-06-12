---
title: "Redirecting back to windows"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by ViralEntity on 2007-02-02
Hi i have recently tried to install linux onto my laptop, but have had issues. In fact i also damaged my CD ROM in a small fall and cant boot from any cd as it wont work. I can get to the grub command so how can i load back into windows?

---

### Post by an.echte.trilingue on 2007-02-02
You hit the escape key at the very beginning of the boot to get the list of installed OSes.  If you want to boot windows automatically or open the menu automatically, you can edit this behavior with "sudo gedit /boot/grub/menu.lst"

Of course, if you uninstalled windows and your cd drive is broken, you are pretty much SOL.

Take care,
-mat

EDIT: By the way, be sure to read the instructions in /boot/grub/menu.lst before you change things or you might end up with an unbootable system, which would be bad if you don't have a CD Drive.

---

### Post by aberry5555 on 2007-02-02
If your windows drive is on the first partition and you installed grub over the windows loader then, when you click windows in the grub, it will just loop back on itself, unfortunately :S I think you are going to have to buy a new cd drive in order to get this to work as you will have to move thre grub the second partition and use the windows recovery console in command line mode to recreate the windows loader. Good luck.

---

