---
title: "Ubuntu hangs with walking points..."
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2011-09-27
How may I see where the booting of the system hang, or in other words, ho to get the classic boot screen there it says what happend then I try boot with live-SD-card.

/cheers

---

### Post by plant pot on 2011-09-27
I am a new Ubuntu user that knows nothing.

I too had ubuntu hang (for half an hour) with walking points, in my case an fsck (disc check) had stuck and the walking points were still walking but too stupid to realise that nothing was actually happening.

I suggest you press the 'Esc' key in the top left of your keyboard. In my case this allowed me to see what was going on. I was then able to signal the broken fsck to stop by holding down 'Control' (or Ctrl) and pressing 'c' once.

Maybe tell us what is printed on your screen when you press 'Esc'?

---

### Post by Azyx on 2011-09-27
Hey. Thanx for the tip on 'esc'.

It says:
```
stdin: error 0
Killed
Killed
Killed
unable to open '/dev/sda'
stdin: error 0
stdin: error 0

```And so on....untill I press ctrl+alt+del

I have tride booth 10.04.1 and 10.04.3 LTS live-SD.

cheers

Edit. I see now another line in above this text, and unable to open '/dev/sda' have disappeared

```
(process:266) GLib-WARNING **: getpwid_r(): Failed due to unknown user id (0)
```

---

