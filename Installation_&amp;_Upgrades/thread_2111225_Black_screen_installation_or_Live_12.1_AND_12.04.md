---
title: "Black screen installation or Live 12.1 AND 12.04"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by ewitte12 on 2013-02-01
I'm trying to get Ubuntu to run/install off USB and its giving me a black screen immediately after choosing either option.
 
System Specs
MSI GT70 0nc
I7 3630Q (HD 4000)
Nvidia GTX 670mx
16GB RAM
 
In BIOS I have secure boot turned off. There is no option to disable discreet graphics. If I go to the command console it lists available modes under the GOP driver and the testvideo option even works. I've also tried editing the CFG file and enabled text mode only and that gives an error about not being able to close EFI. I'm about to just install under VMware since this isn't going to be a primary OS anyway.
 
Eric

---

### Post by Bashing-om on 2013-02-01
Hi ewitte12; Welcome to the forum.

See if this leads to something productive:
Boot the liveCD; Soon as the bios screen clears depress and hold the shift key -> language screen, escape key to accept default -> boot options -> f6 yields a list of preset boot options of which "nomodeset" is generally a good choice.

Once to the desk top:
12.04: launcher (left side of screen) ->System Setting -> Additional Drivers; install the recommended driver.
12.10 ubuntu software center -> software sources (task bar menu) -> Additional Drivers (tab); install the recommended driver.

If the above has positive results, will advise on getting same in the permanent install.
[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

