---
title: "grub-update loses old options"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by kulminaator on 2005-08-18
has anyone got an idea where does grub-update fetch its default kernel options from ?

each time i do grub-update , it rewrites the /boot/grub/menu.lst file and i have to edit it again to add my specific options to there ...

i'm an oldschool lilo boy, but i thought learning how grub works would be educational ...

anyway, i have grepped throu the whole /etc and /grub and i cant find the place where it stores the options :S

i just want to add some custom parameters to the default line but cant find the spot where grub-update picks them from ...

---

### Post by Juergen on 2005-08-18
The parameters are extracted from the comments in 'menu.lst'.
AFAIK that's not normal grub behaviour, but the debian way to do it.

Search for '### BEGIN AUTOMAGIC KERNEL LIST'
The default kernel options should be set in the line starting with '# nonaltoptions='

---

### Post by az on 2005-08-18
...And do not let the "#" scare you.   The line is parsed when grub configures itself, and not when you boot, so the line has to have a "#".

---

