---
title: "Some visual items freezing after upgrading to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by lampak on 2011-05-03
After upgrading to 11.04 I had a few issues. Most of them I've already solved but at least one remains: some visual elements don't refresh and freeze for a very long time, sometimes indefinitely. 

See the attached screenshot: the bottom bar doesn't show Firefox open, the date on the top one doesn't get highlighted by the cursor, the title bar of the Firefox window doesn't name the title of the page I'm visiting. The same applies to the whole desktop. They froze some time ago and stayed as they were. 

Icons on these bars and the desktop are clickable, menus drop down and so on, so they haven't crashed completely, only something is wrong with their displaying. Apps, such as Firefox, work normally. 

The frozen elements sometimes unfreeze (but very rarely). The moment of their freezing is not specified - at other times the bottom bar managed to display the app I ran and froze then etc.

I use ATI proprietary drivers and compiz. I switched back to the Classic Ubuntu Desktop. 

I followed some of the advice from [this page](http://ubuntu4beginners.blogspot.com/search/label/Natty%20Narwhal): I reset X11 config, reinstalled proprietary drivers, disabled syncing to VBlank by compiz (compiz settings reset themselves during the upgrade). I also upgraded all the packages I could upgrade. It solved other problems I had but not this one.

How I hate Ubuntu upgrades :evil:

---

### Post by lampak on 2011-05-20
Most elements fixed themselves. Title bars remained and I've just managed to fix them as well. 

There seems to be a bug in unity-window-manager, at least when run from classic gnome. I've got no idea why compiz-manager decides to run this manager over gtk-window-manager but when I forced using the latter (CompizConfig->Window Decorator->Command) the problem was fixed.

EDIT: I was too quick - the problem is NOT FIXED yet. Title bars of some apps like firefox, which I was most concerned about, were fixed but some (calculator, terminal) were not. 

But the problem is quite minor now.

---

