---
title: "messed up install"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by e-mountaine on 2006-04-11
I formatted a spare HD in XP & installed version 5.10 ubuntu from supplied disk. all went well. disk ejected and rebooted but no grug screen for booting option i tried to reinstall but goes only so far and freezes. now XP does not see the HD so i cannot reformat and start again. i installed the server version  and it works fine except i cannot install gnome( desktop?)

P4 3.0 G.    1Meg RAM  MSI neo 2 mb.  HD 10 G.

no panic have XP still working but would love to get this up and running.

---

### Post by OMRebel on 2006-04-11
How far does it actually load up when performing a regular install?  Does it freeze when trying to load grub?

---

### Post by Kapre on 2006-04-11
[QUOTE=e-mountaine]I formatted a spare HD in XP & installed version 5.10 ubuntu from supplied disk. all went well. disk ejected and rebooted but no grug screen for booting option[/quote] 

On the install, did you select that the GRUB take over your MBR? If you did not, then you'll only have your XP working (as it seems coz you can still boot from it)

>  i tried to reinstall but goes only so far and freezes. now XP does not see the HD so i cannot reformat and start again. i installed the server version  and it works fine except i cannot install gnome( desktop?)

P4 3.0 G.    1Meg RAM  MSI neo 2 mb.  HD 10 G.

no panic have XP still working but would love to get this up and running.

XP doesn't see the HD because it is now formatted (Ext3) as a different system which XP doesnt recognize. For your spare HD, what is the size of it? Did you get your CD from the mail or did you d/l it? If you d/l it, check the md5sum or re-burn it on a slower speed (say 6x-8x) as this might also be the cause that is why its freezing.

K

---

