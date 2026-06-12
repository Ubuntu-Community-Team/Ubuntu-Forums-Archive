---
title: "KDE Loading issue...."
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by ChinaCatJones on 2005-05-02
I'll preface this by stating for the record that I am a Linux newbie.  So if this is a stupid question please forgive my ignorance.  I've spent considerable time trying to track this issue to earth with no success.  And if I have posted this question in the wrong forum, please kindly point me to the right one.

When I first logon I am presented with two errors:

The Composite Manager crashed twice within a minute and is therefore disabled for this session.

and

Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

Any tips on resolving this?

Thanks for your time,

Chris

---

### Post by ChinaCatJones on 2005-05-02
I found this post and it seems to have fixed my issue.

[http://www.ubuntuforums.org/showthread.php?t=19115](http://www.ubuntuforums.org/showthread.php?t=19115)

The pertinent information is near the bottom.

X loads slower now, but the issue is resolved.


Chris

---

