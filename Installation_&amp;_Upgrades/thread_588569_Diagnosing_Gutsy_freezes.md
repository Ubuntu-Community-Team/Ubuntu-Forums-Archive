---
title: "Diagnosing Gutsy freezes?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by homeslice on 2007-10-23
Several days ago I installed Gutsy on my Dell Inspiron 6400, and since then it's been freezing at least once a day. Previously I ran Feisty with no issues. I think the freezes have something to do with xorg or kwin, since all window decorations/titlebars/borders turn solid black. The mouse will move but no windows will respond. CTL-ALT-DEL causes the windows to turn solid gray, but won't bring up a logout button or anything, and I have to force a restart.  
 Both dmesg and /var/log/Xorg.0.log don't report any error messages, and I'm not sure where to begin looking to diagnose the problem. I'm just using the integrated video, so I don't think it's a video driver issue. I don't think it's a hardware problem since Feisty ran just fine. I don't think it's a memory issue either, the swap partition seems to be active. I reconfigured xserver-xorg (dpkg-reconfigure xserver-xorg), didn't seem to help. The install was fresh from a CD (I overwrote Feisty, perhaps unwisely). How does one diagnose something like this?
 thanks

---

### Post by brujoand on 2008-01-11
Hey, I have the exact same problem on a fresh gutsy system. Mouse works, everything else is bricks and stones.. Found many posts on this matter, but everybody seemes to think that this has something to do with nvidia cards. This is not likely since I have an intel graphic card. Also, I made a fresh install of gutsy a month a go and the system never froze.. 
So someone at the ubuntu team messed something up in a update, but nowbody seemes to know what.
Any clues?

---

### Post by brujoand on 2008-01-14
Hm.. Funny thing....
I uncomencted the backports repositorys, did an update and an upgrade woops..  

No more freez.

---

