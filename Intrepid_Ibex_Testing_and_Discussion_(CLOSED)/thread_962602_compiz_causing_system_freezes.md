---
title: "compiz causing system freezes?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2008-10-29
hi,

I've been running intrepid since the beta and had system freezes whenever using anytype of window switcher that used (alt+tab) as the hotkey to switch windows. When switching to metacity everything works fine. Currently the only compiz plugin that works is ring switcher and even then if i change the default shortcut to (alt+tab) from (super+tab) it freezes (although not as much as the other switcher plugins)...anyways...i recently did a clean install to the RC and this problem still persists...anyone else have this prob? fixes?

---

### Post by jerrylamos on 2008-10-29
Compiz freezes this IBM Thinkpad R31 even on boot.  See Launchpad bug 259385.  The eventual fix is to have compiz blacklist some graphics hardware like mine.

A way to tell if compiz is doing it to you is to:

start a terminal session
metacity --replace &

I don't remember if sudo is required as a prefix.

The way I handle it is

boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

Works for me.  You can try installing compiz again from synaptic if you wish,

Jerry

---

### Post by inportb on 2008-10-29
I don't think you should use sudo. As a KDE user, I can't really offer any knowledge regarding compiz, but removal seems to be a common route.

---

### Post by myddewji13 on 2008-10-29
so let me get this straight...basically you're proposing that I remove compiz then reinstall it? Sorry I'm kinda confused

---

