---
title: "I can't read anything in my ubuntu..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by house7 on 2007-04-21
all my font/letter/words is gone. Suddenly i can't read anything. It just a square typo (in all application) except on Firefox.. but all the title, words in ubuntu is squared.. OMG.. i don't know what to do....

All happens because i restart my laptop after update is complete (well, not all complete) because my internet connection was stopped suddenly...

Please help... I'm using Edgy going to upgrade Feisty...

---

### Post by spin2cool on 2007-04-21
Your problem is that the update didn't finish correctly.  Try this:
[http://ubuntuforums.org/showthread.php?p=2322201#post2322201](http://ubuntuforums.org/showthread.php?p=2322201#post2322201)

---

### Post by house7 on 2007-04-21
It doesn't work either, i upgraded 200+ package but the typo is still square.... :((

---

### Post by digitalis on 2007-04-21
Yup, my world's gone all square as well, after upgrading 6.10 to 7.04.
Presuming it's a font issue of some sort.
There's an error message after login, but, of course, I can only guess at it's contents due to all the text being little square boxes.
Update manager has stopped working from the menu as well, for some reason.
Will do a bit more digging to try and get it fixed.

S.

---

### Post by house7 on 2007-04-21
Does it connected with Phyton, Pango issues?? Well i hope somebody can answer it soon coz i need the laptop for my thesis.. oohh... T_T;;;;;;

---

### Post by digitalis on 2007-04-21
> **house7 said:**
> Does it connected with Phyton, Pango issues?? Well i hope somebody can answer it soon coz i need the laptop for my thesis.. oohh... T_T;;;;;;

Seems to be, I get the following when trying to upgrade again from cd - 

> ubuntu:~$ gksu "sh /cdrom/upgrade"

(gksu:5424): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

(gksu:5424): Pango-WARNING **: pango_shape called with bad font, expect ugly output

Haven't got much further than that, though.

S.

---

### Post by house7 on 2007-04-21
What am i supposed to do now?? I'm really stuck here.. :confused:

---

### Post by digitalis on 2007-04-21
Try doing the upgrade manually, like it says here - 

[https://help.ubuntu.com/community/FeistyUpgradesManual]("https://help.ubuntu.com/community/FeistyUpgradesManual")

Seemed to work for me - just gotta get X/nvidia/Envy sorted on the upgraded kernel version, but I'm currently in the version that had the squares, and they're gone, so should work for you, hopefully.

S.

---

### Post by house7 on 2007-04-22
Digitalis, That's a good news.. Which one to do first? Uninstalling pango-libthai? or just follow the instruction?

---

### Post by digitalis on 2007-04-22
> **house7 said:**
> Digitalis, That's a good news.. Which one to do first? Uninstalling pango-libthai? or just follow the instruction?

I just followed the instructions - the only thing it didn't fix was the nvidia drivers (for a 6800 - I'd been using the Envy script), but an install of the latest version of Envy fixed that.

Looks like we were both stuck with a partial upgrade which was sitting on top of the previous kernel version (if that makes sense), so, you have to complete the upgrade (including upgrading to the new kernel) for it to work properly.
Hope you get it sorted.

S.

---

### Post by house7 on 2007-04-22
Got that fixed, thanks a lot.. :)  Now i'm on 7.04, and enjoy it..... Kinda hard desicion to make because i have the Live CD and prepare to clean install..

---

### Post by pepsi_max2k on 2007-04-22
ahh... squares... I got them in system > prefs > shared folders. is there a specific font i'm missing? everything else is fine :s

---

### Post by MrMacHead on 2007-04-24
I ended up with the missing system font problem as well, after some glitch occured in my Feisty upgrade. This is the fix that worked for me, thanks to a thread on this forum...

sudo apt-get dist-upgrade

---

