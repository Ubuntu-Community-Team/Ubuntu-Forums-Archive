---
title: "Newbie - Buffer I/O error"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by diesela4 on 2008-07-05
[FONT="Tahoma"]Hello folks, i have been trying to install 8.04.1 today to no avail. 
Below are the machine specs:

Abit AB9 Pro Motherboard
Intel E6600 1.8Ghz Dual Core
ATI X19050 Pro GFX Card
3 HDs
1 DVD-RW drive
No Floppy Drive
Windows Vista Installed

I get the CD to boot find and loads me at the menu to select &#8220;Install Ubuntu&#8221;, I hit it and the orange progress bar shows for a few min then the screen becomes test with the flowing error:
&#8220;Buffer I/O error on device fd0 &#8211; logical block 0&#8221;

It does show other stuff but it keeps looping to the above error and sits there spooling out text then back to the error

Thoughts??

cheers[/FONT]

---

### Post by Partyboi2 on 2008-07-05
It looks like it trying to find the floppy drive, try adding "all_generic_ide" as a boot option.
At the main menu press F6 and add at the end of the line
```
all_generic_ide
``` then enter.

---

### Post by sdennie on 2008-07-05
You may also want to check if the BIOS thinks there is a floppy drive hooked up.  If so, disable it.

---

### Post by diesela4 on 2008-07-06
got the floppy sorted, disabled it in the bios but now am getting a new screen with BusyBox on it and just a cmd line interface

now am lost

---

