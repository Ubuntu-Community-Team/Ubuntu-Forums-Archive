---
title: "Some keys on my laptop have incorrect key codes"
date: 2008-08-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-08-06
I have a Dell Precision M90. Until a few days ago, my keyboard was working fine. Now, the cursor keys don't respond, and the multimedia keys at the front of the laptop, and delete, page up, end, etc, don't work either.

Thing is, they do work, but all the keys that don't work, have in fact, the wrong key codes. This, I proved using xev.

How do I fix this?

---

### Post by klange on 2008-08-06
I believe a switch to evdev was forced (I may be wrong), as selecting "evdev Managed Keyboard" as the layout in gnome-keyboard-properties has my keyboard running properly (had to restart some apps that have internal keybindings, ie. Compiz). Xorg.0.log also reports nothing when grep'd for "kbd".

I myself had to reassign my keyboard shortcuts for my media keys, as they all started to appear with the proper X86___ symbol names rather than seemingly random keycodes.

---

### Post by Nullack on 2008-08-07
So whos bugged it and whats the number? :)

---

### Post by ronacc on 2008-08-07
I've got this one too , I added comments to this bug# 255008 .

---

### Post by ronacc on 2008-08-07
note ! after last nights late updates (august 6 ) my keyap (generic qwerty us ) seems correct again .

---

### Post by phenest on 2008-08-07
Check [bug 255008]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/255008") for how to fix this. Worked for me and others.

---

