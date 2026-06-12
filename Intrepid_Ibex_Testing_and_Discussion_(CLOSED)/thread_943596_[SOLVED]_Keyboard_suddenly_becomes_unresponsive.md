---
title: "[SOLVED] Keyboard suddenly becomes unresponsive"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-10
I've gotten a bug I had in beta Hardy and Gutsy as well (can't remember witch)

Suddenly my keyboard gets completely unresponsive, and the caps lock light is blinking. Nothing reacts on anything, have to kill the power.

---

### Post by inportb on 2008-10-10
That'd be a kernel panic. What're the circumstances that lead to this event?

---

### Post by lukjad on 2008-10-10
Please ignore this post.

---

### Post by olavjunior on 2008-10-10
I don't know what causes it. It just happens, the laptop can be standing unused and then it's suddenly locked. I'm trying to figure it out by killing processes. Just hoped someone else had figured it out.. 

Any ways to track this other than killing processes?

---

### Post by olavjunior on 2008-10-10
Well, did some more searching, and it seems that it was n-networks that did it. 

EDIT: I just upgraded to the latest kernel, but that didn't help :(

---

### Post by ktp on 2008-10-10
I am seeing something similar...it seems like the screen locks up.  But I can kill X and everything works again.

---

### Post by olavjunior on 2008-10-12
The  kernel panic is due to surfing on n wireless networks. See this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

I hope this gets solved quickly since many of the networks I use are n.

---

