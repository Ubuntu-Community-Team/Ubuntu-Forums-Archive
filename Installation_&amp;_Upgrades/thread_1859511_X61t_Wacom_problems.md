---
title: "X61t Wacom problems"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Joejo on 2011-10-13
So I installed 11.04 on my Thinkpad X61t and after some work I got everything working just fine (the pen function worked fine and the rotation was working great also). But then the new upgrade came out (11.10) and everything went ok, restarted, checked to see if the wacom worked and the hotkeys worked fine. The rotation still worked but then there was a problem in portrait mode. The wacom input mirrored the pen, e.g. if I place the pen at the bottom in portrait mode the arrow appears at the top and vice versa. 
Is there a solution for this? I would like to know.

---

### Post by Favux on 2011-10-14
Hi Joejo,

Yes.  The default xf86-input-wacom-0.10.0 of Oneiric has the same bug as the 0.10.11 in Natty.  Cw and ccw are swapped so portrait orientation for the input tools is reversed.  The fix is to upgrade to at least the 0.11.1 tar because the upstream fix is in it.  See part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  See this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647)

---

