---
title: "Problem with gedit after 8.04 -&gt; 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by iKevin on 2008-11-02
Hi All

I am having a few problems after the upgrade, nvidia driver faulure being the biggest issue since I need accelerated 3D.  There are lots of posts about that so I can wait for a fix.  However, I am having trobles with "gedit".  It takes about 30 seconds to start.  When I launch it, a frame appears without the normal menus.  30 seconds later that menus appear.  Below is the timing after launching from a shell and quiting as soon as the menus popup.

$ time gedit

real	0m33.797s
user	0m28.742s
sys	0m1.912s

Is this do to my system being in ubuntu "low graphics" mode?

Kev

---

### Post by robertyou on 2008-11-17
It's a bug from gedit's plug-in "File Browser pane". You can un-check it from:

Edit -> Preferences -> Plug-ins

---

