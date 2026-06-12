---
title: "Transmission and banshee indicator applet bug"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ljrmorgan on 2010-04-14
I've been using the application indicator extension for banshee which makes it use the new style indicator applet thing instead of the old system tray icon. Transmission now has an application indicator instead of a system tray icon too.

So now the problem: Both programs have a "Show <app-name>" option in the application indicator menu which can be ticked. Presumably the idea is that the window is open if and only if there is a tick next to "show <appname>".

However, say I launch transmission and close the window (no tick next to "Show transmission"). If I then click on the transmission icon in Docky, transmission opens again, but the "Show transmission" menu remains unticked. Now if I close the transmission window, the "Show transmission" option gets ticked again! Basically the tick is there precisely when it shouldn't be.

With banshee if I have the window closed and click the icon in Docky banshee pops open but "Show banshee" remains unticked. Unlike with transmission though when I close banshee "Show banshee" remains unticked.

Does anyone else have this problem? If so I'll file a bug.

---

