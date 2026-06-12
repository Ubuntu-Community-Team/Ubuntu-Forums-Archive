---
title: "Nautilus visible columns bugged"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-09-11
Well, I filed the following bug almost 2 months ago and still seeing it with a clean install of karmic daily live CD from today, 2009.09.11:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/401414](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/401414)

It could use a push as it's a usability regression from previous releases. To sum up from one of my comments in the bug:

> 
Here's more specific STR:

1) Open nautilus. Select View > Visible Columns...
2) Highlight "Name". Press [Move Down]. NOTE: nothing happens - no visible change in display
3) Press [Move Down] again. NOTE: "Name" column moves down (to the right) one column position
4) Press [Move Up]. NOTE: "Name" column moves down (to the right) one column position.
5) This will continue indefinitely, with the desired action always one step behind what is show in the nautilus window.

You can close the "visible columns selector" at any time and press [F5] to get the layout you actually selected.

This is a seriously confusing usability issue and unless a user is aware that every change is lagging by one action, it's pretty hard to customize the nautilus window to your liking.
 

Please note you need to be viewing a directory in list view to get the visible column option. If some more people could confirm this with "this affects me too" in the bug report, maybe it would draw more attention and have a revised bug filed upstream.

---

### Post by VMC on 2009-09-11
It works for me. I see the change taking place as I move "Name" down. Maybe in conjunction with another option this gets messed up. Any replies at LP to your report?

---

### Post by tekstr1der on 2009-09-11
I initially thought it may be something due to the fact that my system has seen several distribution upgrades. That's why I did a clean VM install of today's daily.

With all settings completely default for nautilus except displaying in list view format, this issue is replicated every time by following the above steps. You can verify this bug using a live CD of alpha 4, alpha 5 or daily.

---

