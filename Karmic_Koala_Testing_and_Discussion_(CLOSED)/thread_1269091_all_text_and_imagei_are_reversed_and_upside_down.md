---
title: "all text and imagei are reversed and upside down"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-09-17
I just did a distribution upgrade to karmic and take a look at what happened!

every menu item, dialog box, all text is reversed. windows are upside down
This is a programming joke?
how do i fix it??

---

### Post by Eestlane on 2009-09-17
Try alt+F2
gnome-display-properties
and change rotation

---

### Post by Amaranth on 2009-09-17
Looks like you have intel hardware but installed the nvidia driver.

---

### Post by sdowney717 on 2009-09-18
ok, I have ati x1300

i tried running display-properties, but it says normal rotation and none of the buttons are clickable

the only way I can make sense of the screen is if I use a mirror and then it is upside down.
so how do i purge nvidia driver??

---

### Post by sdowney717 on 2009-09-18
I tried sudo apt-get --purge remove nvidia*

and it removed nvidia packages.

however, gui still shows everything reversi.

i tried logging in as another user and still the same.
i tried sudo dpkg-reconfigure xserver-xorg and still the same

---

### Post by sdowney717 on 2009-09-18
bump, any ideas?

---

### Post by MacUntu on 2009-09-18
Try removing 'xserver-xorg-video-nv'.

---

### Post by sdowney717 on 2009-09-20
I finally fixed it by formating and reinstalling alpha6.
It is working well.

Why the NV driver cause a flipping when I have an ATI x1300? Why would it not be using the ati driver and why would the nv driver be involved at all?

---

