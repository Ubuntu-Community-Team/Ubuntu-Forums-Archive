---
title: "Problems with Lucid"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by darkhole on 2010-02-21
Hi guys, ok I'm testing Lucid Lynx on my PC. 

I have some problems and I want to know if there are reported Bugs about this different problems:

1. Windows without borders now have borders, app like Sticky notes or Audacious (Selección_005.png). Even the GDM Login Screen has a border with minimize icon.
BUG: [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524869](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524869)

2. The Switching of users is becoming crazy, when I choose another session, and log into, the other session appear and disappear every time that I press keys. My session have a shortcut to Scale plugin from Compiz at a corner of the screen. In the other session I can see my windows simply going with the mouse to that corner. Even use my windows without enter any password. [PARTIALLY SOLVED]

3. Switching between session have another problem. Sound didn't work in the second session. And checking volume settings, seems like the hardware was unrecognized. I got Dummy output, no my real hardware.
[SOLVED]

4. My old pen drive (similar to phpThumb_generated_thumbnailjpg.jpeg)  doesn't work, seems like if were recognized, but can't mount it. Seems familiar to this bug, I'm adding info to this bug: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66239](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66239)
UPDATE: BUG: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/518186](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/518186)

5. Switching session gave me 2 cursors, one «false» and one true cursor, I can merge both cursors going to the upper left corner. But after sometime they start to split again. This also cause multiple actions in both session, seems like first session is still active. [SOLVED]

6. Error on boot about "unknown key ACTION": [http://ubuntuforums.org/showthread.php?p=8851818](http://ubuntuforums.org/showthread.php?p=8851818) Problem can be fixed but there is now a bug report.
BUG [SOLVED]: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433)

I hope somebody can gave some more info to detect, help to fix this bugs...

---

### Post by darkhole on 2010-02-21
Oh, I forgot to mention my system specs.
Ubuntu 10.04 64 Bits
GeForce 6200 video card using nVidia proprietary driver (195.36.03 from repos)
Compiz enabled (on all sessions)

System completely updated. :)

---

### Post by OrangeCrate on 2010-02-21
This is the best place to check on, report, and keep track of bugs...

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by darkhole on 2010-02-21
> **OrangeCrate said:**
> This is the best place to check on, report, and keep track of bugs...

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

I know :) But, I'm asking for references, before report any bug I like to listen another voices with same/similar problems. I can't saturate Launchpad/Ubuntu with bugs without arguments.(I just reported the typo error on xserver-xorg-video-intel).

---

### Post by joey-elijah on 2010-02-21
The first one i certainly experience also.  Even simple things like thumbnail previews in firefox (via an addon) now have a Metacity... 

[IMG]http://img14.imageshack.us/img14/5805/screenshot1hq.png[/IMG]

it's a curious little issue..

---

### Post by psyke83 on 2010-02-21
Point number one is related to the new client-side windows patch. Bug [#524869]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524869").

---

### Post by darkhole on 2010-02-22
> **joey-elijah said:**
> The first one i certainly experience also.  Even simple things like thumbnail previews in firefox (via an addon) now have a Metacity... 

[IMG]http://img14.imageshack.us/img14/5805/screenshot1hq.png[/IMG]

it's a curious little issue..

Hey, here is the reported bug, they are working on it.
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524869](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524869)

---

### Post by darkhole on 2010-03-02
Some problems are still there. But, many bugs has been fixed.

---

