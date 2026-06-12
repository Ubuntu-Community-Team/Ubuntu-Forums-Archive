---
title: "Clean 11.04 Install, Backlight on Notebook Won't Turn On"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by foresthill on 2011-05-08
I did a clean install on my Gateway NV7802 notebook.

Graphics are Mobile Intel GMA 4500MHD. Screen resolution is 1600 x 900.

I can see GRUB fine, but when I boot up I can just barely make out the log in screen, If I hit enter, and then type in my password, then hit enter again, I can get to the desktop, but still cannot get the backlight to turn on.

I can connect an external monitor, and that works good enough for me to enter terminal commands and putz around a bit.

I ran the update manager, hoping the devs have fixed this bug, but as of the morning of 5-8-11, bringing my updates current did no good. 

A Google search shows no fixes so I guess I'm gonna have to wait this out until someone figures out what the problem is and patches it in the updates. 

Anyone have a proven fix for this? Please, no endless random terminal commands that accomplish nothing, an actual fix is what I'm looking for. 

It's kinda tough to use my computer when I can't even see the screen. :(

---

### Post by MAFoElffen on 2011-05-08
> **foresthill said:**
> I did a clean install on my Gateway NV7802 notebook.

Graphics are Mobile Intel GMA 4500MHD. Screen resolution is 1600 x 900.

I can see GRUB fine, but when I boot up I can just barely make out the log in screen, If I hit enter, and then type in my password, then hit enter again, I can get to the desktop, but still cannot get the backlight to turn on.

I can connect an external monitor, and that works good enough for me to enter terminal commands and putz around a bit.

I ran the update manager, hoping the devs have fixed this bug, but as of the morning of 5-8-11, bringing my updates current did no good. 

A Google search shows no fixes so I guess I'm gonna have to wait this out until someone figures out what the problem is and patches it in the updates. 

Anyone have a proven fix for this? Please, no endless random terminal commands that accomplish nothing, an actual fix is what I'm looking for. 

It's kinda tough to use my computer when I can't even see the screen. :(
Will fix some backlighting Problems:
> **glococo said:**
> Hi,
The best workaround for solving backlight ISSUE was for me:
  Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local
```
gksudo gedit /etc/rc.local
```2) Add the command before EXIT 0
```
setpci -s 00:02.0 F4.B-0
```3) Restart.
You should now be able to boot in UNITY where nomodeset was unable.

---

### Post by foresthill on 2011-05-08
[PHP]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setpci -s 00:02.0 F4.B-0

exit 0[/PHP]

Added text as shown above. Backlight still does not work. :(

---

