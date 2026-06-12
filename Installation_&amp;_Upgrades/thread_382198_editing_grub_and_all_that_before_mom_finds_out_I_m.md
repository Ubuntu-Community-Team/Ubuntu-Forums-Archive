---
title: "editing grub and all that before mom finds out I messed up XP!!"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by slugkilla on 2007-03-11
OK so I installed edgy on a new drive and have xp on the other. I installed edgy with the xp drive unattached. Currently the egdy is on master and XP is set to slave. I want to set it up so that XP runs when the comp is cut on and edgy can be selected to run via grub. Thanks a lot.

---

### Post by bernied on 2007-03-11
You just need an entry in the /boot/grub/menu.lst file like this:
```
title windows
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
boot
```
Does it work?
If it does, put it before all the automagic stuff, set the default to 0 (should be at the beginning of the file) and remove all the savedefault lines.

Then have a look at the automagic area and figure out how to stop the savedefault lines from reappearing when you next upgrade your kernel.
[EDIT] You probably don't need to do this, just make sure that the windows entry is set as default and there is no line that says 'default saved' [/EDIT]

Don't listen to anyone who tells you you have to swap the drives and do 'setup (hd0)' in grub - this will wipe your windows MBR which is not necessary.

---

### Post by bernied on 2007-03-11
I should have said:
- use hiddenmenu to hide the grub menu - you have to hit Esc at boot to get to the menu
- set the timeout really low - like 2 or 1, you will have 2 or 1 seconds to hit Esc to access the grub menu.

You should also make yourself a grub cd, or even better a grub usb stick. You can boot from this when things don't go to plan.

---

### Post by confused57 on 2007-03-11
bernied is right, place your Windows entry above the ###BEGIN AUTOMAGIC..., as described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Following his advice for hiddenmenu & 2-3 seconds timeout, no one will be the wiser you even have Edgy installed.

---

### Post by slugkilla on 2007-03-11
Thanks a lot! I'm still in a lot of trouble because mom thinks linux is slowing down her comp, but I'm happy about it.

---

