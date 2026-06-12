---
title: "Live CD - no mouse cursor"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike Easter on 2009-10-15
Karmic 9.10b

Graphics problems on bootup resolved by using vga=795 in boot commandline-- this results in a desktop with no mouse cursor.

Mobo ECS 7050M-M [MCP68] which is an nVidia chipset GeForce 7050 + nForce 630a.

Is there some kind of command I can put into the boot so that I can get a mouse cursor so that I can install and use the nvidia drivers?

I saw some different kinds of problems with nvidia chipsets which needed to handle the hardware cursor, but I don't know how to do that with the bootup.  I've tried alt-ctrl-F1 alt-ctrl-F7 or F8 but the cursor doesn't appear.

Tnx in advance for any help.

---

### Post by Mike Easter on 2009-10-15
Ub 9.04 or Mint7 live CD boot satisfactorily and install and can take nvidia drivers.  There is no problem with live CD bootup missing the cursor.

---

### Post by Mike Easter on 2009-10-18
> **Mike Easter said:**
> 

Is there some kind of command I can put into the boot so that I can get a mouse cursor so that I can install and use the nvidia drivers? 

How can I use a boot command to turn off the HWCursor in favor of the SWCursor?

Without a visible mouse cursor, it isn't possible for me to do anything.

This is a regression from Ub 9.04 which didn't have this mouse cursor problem on bootup with this same hardware.

---

### Post by Mike Easter on 2009-10-19
How can I use reconstructor to edit/modify the karmic .iso so as to have nvidia drivers?

---

