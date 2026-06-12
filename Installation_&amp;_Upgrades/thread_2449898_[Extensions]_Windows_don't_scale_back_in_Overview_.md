---
title: "[Extensions] Windows don't scale back in Overview after upgrade to 20.04"
date: 2020-09-03
forum: Installation &amp; Upgrades
---

### Post by prkos on 2020-09-03
My upgrade to 20.04 wasn't without errors but it seems that it was ironed out through repeated attempts. 

The only problem I have is that viewing windows "thumbnails" (minimized versions) in Overlay (Super key) don't work. 

When go into Overview the windows stay in place as if I hadn't gone into Overview. They keep their position and size. I do see that I'm in Overview because the dock? on the left, the dash? on the right and the search bar on top become visible. They are animated into view, and animations work generally speaking. 

Here are the screenshots for regular (top) and Overview (bottom): 

[[img]https://i.ibb.co/JjzgRTV/overlay-Gnome-Windows-Bug.png[/img]](https://ibb.co/JjzgRTV)

When I disable Extensions globally in the title of Tweaks window the Overview windows work as expected! 

But when I enable Extensions globally, but not one is enabled individually, the windows in Overview don't work! 

Could this be caused by one extension even when it's not enabled, but only installed?

As far as I can tell all the Extensions work as expected, when they're enabled. 

One other symptom that may be related: In KOrganizer there is a preference to use System colors. If I change that setting on Apply or Ok KOrganizer crashes. It used to work on previous Ubuntu without problems but always causes KOrganizer crash after using it, and the style is always stuck on the System colors (ugly). 

Are there any hints what might be causing this? Without completely uninstalling all extensions and reinstalling and configuring?

---

### Post by dragonfly41 on 2020-09-04
I do not have Kubuntu but I am still learning the ropes on the Ubuntu 20.04 layout options. I had Gnome-flashback in use in Ubuntu 18.04.
However my SuperKey does create overview of tiled windows .. but not a duplicate of the left dock panel on right side. Instead I see a thumbnail of a window.

Do you have this Dash to Dock extension installed?
[https://askubuntu.com/questions/975387/why-do-i-have-two-docks-in-ubuntu-desktop-with-gnome-3-after-installing-dash-t](https://askubuntu.com/questions/975387/why-do-i-have-two-docks-in-ubuntu-desktop-with-gnome-3-after-installing-dash-t)

If so, disable it.

---

