---
title: "Hardy Heron:  remove Firefox Beta"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by gargouille on 2008-05-05
PROBLEM:  many of the Firefox plugins that I use do not function in Firefox beta 3

FIX:  remove Firefox beta 3 and install Firefox 2

If someone has a better way of doing this please post a reply.  This has worked for me, but the fonts are not as readable:

1. Launch Synaptic Package Manager and mark for complete removal:
-firefox
-firefox-3.0
2. Apply
3. Install:
-firefox-2
-firefox-2-gnome-support
-firefox-themes-ubuntu
-ubufox
4. Apply

---

### Post by octoberdan on 2008-05-05
You could create two profiles, one for use in firefox-2 and one for use in firefox-3. Just a thought. Oh, and upgrade your system, we're up to firefox-3b5 ;-).

I'm not quite sure how to address your font issue. The following may be relevant:
[http://ubuntuforums.org/showthread.php?t=588091](http://ubuntuforums.org/showthread.php?t=588091)

Or maybe you need to install msttcorefonts?

---

### Post by gargouille on 2008-05-05
Octoberdan,

I did mean to say Firefox 3 beta 5.  Thanks for finding my mistake.

Also thanks for the link.  What I did to address the problem:

1. change the minimum font sizes to 13 in Firefox:  Edit > Preferences > Content > Fonts & Colors section > Advanced.
2. Install Microsoft Core Fonts from Add/Remove
3. In Firefox:
type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox
4. Change font settings
4a. System > Preferences > Appearance
4b. Font tab, then click on Details under Rendering
4c. Hinting section enabled the None radio button



Also I found another thread on removing Firefox 3 Beta 5:
[http://ubuntuforums.org/showthread.php?t=767012](http://ubuntuforums.org/showthread.php?t=767012)

---

