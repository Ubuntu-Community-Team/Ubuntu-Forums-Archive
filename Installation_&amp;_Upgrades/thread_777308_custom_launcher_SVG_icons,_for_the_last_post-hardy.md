---
title: "custom launcher SVG icons, for the last post-hardy upgrade thing to fix..."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2008-05-01
I upgraded from feisty to hardy! and it was very hard, I dealt with virtualbox not working anymore, 3d acceleration and the keyboard using a bad language settings, now all of that is working nicely. But  a problem remains, custom SVG icons given to launchers do not render correctly anymore in the desktop.

So, to explain easily, I am attaching an SVG, and cuts from my desktop screenshots in feisty and hardy of the same lanucher, new gnome seems not to like to render SVG anymore. Is there a patch or some option to fix this regression?

---

### Post by drQ.11235 on 2008-11-17
I have exactly the same problem (in hardy).

Launchers will have bitmap rendered svg icons, even when using distribution icons which work fine otherwise, on their usual mime-type icons.

Also the 'Create Launcher' screen will not show any svg icons when browsing for an icon to use.

Did you find a solution?

---

### Post by vexorian on 2008-11-20
I rendered the svg as large PNGs then used the PNGs for their icons.

I like to think I've helped to fix [Bug #529371](http://bugzilla.gnome.org/show_bug.cgi?id=529371) anyway, I was wondering if Intrepid comes with this fix, perhaps the package freeze happened before it was released.

---

