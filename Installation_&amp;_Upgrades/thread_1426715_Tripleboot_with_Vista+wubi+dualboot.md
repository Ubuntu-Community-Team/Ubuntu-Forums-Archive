---
title: "Tripleboot with Vista+wubi+dualboot?"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by Azeno on 2010-03-10
I´m currently a Windows Vista user, and would like to get test some linux distributions - Ubuntu is one of them, Ubuntu Studio is another. 

Iinstalling muliple OS's becomes overly complicated on my old vista machine. Therefore: 

Can I simply turn a regular dualboot into a "fake" triple boot by adding wubi to Vista? Should wubi be installed before the dual boot distro or vice versa? 

Does it make any difference what the "real" dual boot distribution is? I would like to test Ubuntu Studio (not included in wubi) and OpenSUSE. Is either of them better to test first, because they do a better job in easily replacing an old distribution in a dualboot etc.? 

Thank you very much!

---

### Post by superarthur on 2010-03-11
I can only boot into wubi after booting into my Vista partition in GRUB. It's alright for me to have vista, wubi and ubuntu on the same computer. If I want to boot Ubuntu, I just select it in the GRUB, same for Vista. After selecting Vista I have a choice to select between Vista and wubi.
Hope it helps.

---

### Post by DasEi on 2010-03-11
I really wouldn't recoomed wubi, if you just want a look, use a live-cd for a glance, or use unetbootin for windows and do a usb-install, more convienent. (pendrivelinux, if usb shall be writeable, too)
It is possible to boot more than enough OS'es from one harddrive, if space is sufficient, but I want to suggest you install virtualbox and try few distros out in there, then select and install 2 or three permanently in a dualboot.

---

