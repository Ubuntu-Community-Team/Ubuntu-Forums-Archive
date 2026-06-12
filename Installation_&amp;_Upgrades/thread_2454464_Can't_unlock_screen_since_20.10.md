---
title: "Can't unlock screen since 20.10"
date: 2020-11-30
forum: Installation &amp; Upgrades
---

### Post by troffasky on 2020-11-30
[This is Kubuntu. I did pick [kubuntu] from the dropdown, but to no avail, apparently]

I have upgraded to 20.10 and since then, I am unable to unlock the screen from the GUI. 
When locked, it's like the screen is frozen [or, er, locked] - I can see all my applications and I can move the mouse around but there is no UI to unlock it. I have tried different wallpaper types in the Appearance tab of the Screen Locking settings but it makes no difference.
The only way I can get back in is to switch to a console and use loginctl unlock-session. 
Nothing interesting is logged in journalctl when locking and unlocking. Where else can I look for logs?

---

### Post by DuckHook on 2020-11-30
*Thread moved to **Installation & Upgrades** as the more appropriate forum.*

---

### Post by troffasky on 2021-01-08
Somebody else reported the same issue on a Reddit thread, no clues.
I tested a Kubuntu live USB stick and it didn't have the issue. I attempted to do a "repair" of my install from the USB stick but unfortunately wiped my encrypted drive, so ended up reinstalling. Don't have the issue any more.

---

### Post by ActionParsnip on 2021-01-08
I'd test it for a few days. If all is well then please mark as solved

---

