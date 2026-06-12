---
title: "Vista Doesn't Quite Boot Right"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by CadMasterAdam on 2007-04-09
_Background:_
[LIST]
[*]1. install of Vista Home Premium
[*]2. install Ubuntu 6.06
[/LIST]

_Desired result:_
[LIST]
[*]Dual Boot vista/ubuntu
[/LIST]

_Problem to over come:_
[LIST]
[*]Insert entry into menu.lst (see end)
[/LIST]

_Unexpected result:_
[LIST]
[*]partially boots to vista "meaning it only gets to the black screen with the green scrolling progress indicator... and STAYs there."
[/LIST]

_Query_
[LIST]
[*]any suggestions?
[/LIST]

_menu.lst entry:_
[LIST]
[*]title Microsoft Windows Vista Home Premium
[*]rootnoverify (hd0,0)
[*]savedefault
[*]chainloader +1
[/LIST]

---

### Post by zvacet on 2007-04-09
[http://ubuntuforums.org/showthread.php?t=371530&highlight=vista]("http://ubuntuforums.org/showthread.php?t=371530&highlight=vista")

---

### Post by LukeCarrier on 2007-04-09
Hi,

WINDOWS NEVER BOOTS RIGHT, THAT'S WHY EVERYONE HERE USES UBUNTU!

---

