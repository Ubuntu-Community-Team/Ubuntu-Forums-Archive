---
title: "Quadrapassel bugs"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2010-02-28
Can anyone confirm the following bugs in Quadrapassel 2.29.6 (a tetris clone in Lucid):
1) High scores are not displayed.
2) If you go to Terminal and enter 
```
$ quadrapassel

(quadrapassel:18941): ClutterGLX-CRITICAL **: Unable to make the stage window 0x420002d the current GLX drawable

(quadrapassel:18941): ClutterGLX-CRITICAL **: Unable to make the stage window 0x420004a the current GLX drawable
```

Yet the game plays fine.

---

### Post by yoasif on 2010-02-28
added the first bug to launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/529557](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/529557)

you can confirm it (set to confirmed).

---

### Post by Kevbert on 2010-03-01
First bug already confirmed by someone else. Added a note and subscribed.
Thanks.

---

### Post by Rob2687 on 2010-03-01
I don't know if this would be considered a bug but at the higher levels the game is literally impossible to play. At like level 10 the fall speed of the piece is faster than the controls respond. So even holding the left arrow constantly the piece won't reach the side until it is 2/3 of the way down the box. Obviously it's supposed to be hard at higher levels but any tetris clone i've ever played doesn't lag in the controls like that.

---

### Post by Kevbert on 2010-03-03
First bug fixed in quadrapassel (1:2.29.91-0ubuntu2). The second bug still exists.
Rob2687, what are your system specs ? Are you running anything in the background ?

---

### Post by Polniy on 2010-03-03
> **Rob2687 said:**
> I don't know if this would be considered a bug but at the higher levels the game is literally impossible to play. At like level 10 the fall speed of the piece is faster than the controls respond. So even holding the left arrow constantly the piece won't reach the side until it is 2/3 of the way down the box. Obviously it's supposed to be hard at higher levels but any tetris clone i've ever played doesn't lag in the controls like that.
Once I've filled a bug about this in the upstream, but they have said it's ok. So no hope.

---

### Post by Kevbert on 2010-03-21
The second bug report is [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/529479") and has been reported upstream.

---

### Post by michaeldt on 2010-03-22
I get the second bug but the game is unplayably slow. crashes when i try to change settings.

---

