---
title: "Ubuntu 10.4 driver issue heroes of newerth"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aloprot on 2010-03-28
I just updated to 10.4 and wanted to run heroes of newerth. Suddently after I updated from 9.10 the game doesn't want to work. While executing it from the terminal I get the following error:""K2 - Fatal Error: ARB_vertex_buffer_object not available." Now i get 
"warning: The VAD has been replaced by a hack pending a complete rewrite
Floating point exception (core dumped)
"
Why and how can i fix this? Thank you.
Ps:I had the drivers installed, they also have a green thick on ubuntu software center(i have a ati hd4330)but in restricted driver manager it doesn't list it only my network driver. Could this be a problem?
Thanks!

---

### Post by Silvertones on 2010-03-28
Doesn't answer your question but why is a newbi running a Beta version of an OS that is tricky to begin with?

---

### Post by aloprot on 2010-03-28
To help the community, catch bugs, report issues?

---

### Post by aloprot on 2010-03-28
No one can help me with this issue? I tried irc but had no luck....

---

### Post by Sef on 2010-03-28
Moved to Lucid Forum.

---

### Post by bebox on 2010-04-05
i used this patch:[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256"), to fix compiz maximize/minimize delay...and it worked but now i have the same problem...when i start HoN i get: "K2 - Fatal Error: ARB_vertex_buffer_object not available."

or when i start sauerbraten i get:"WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)" and "cannot find shader definitions"

i have ubuntu 10.4 beta with xorg 1.7.6 and ati mobility radeon hd3470 with fglrx.

---

### Post by Xpander69 on 2010-04-05
getting same error. i gues its because that early catalyst 10.4
using ati HD 5770

---

### Post by Ellipsis on 2010-04-05
Same error here with ATI 4670. Probably due to the beta driver... they will get it sorted out by the time they release at the end of the month.

---

### Post by zekopeko on 2010-04-05
> **Ellipsis said:**
> Same error here with ATI 4670. Probably due to the beta driver... they will get it sorted out by the time they release at the end of the month.

Not going to happen if you don't report it.

---

### Post by bebox on 2010-04-06
i think that has nothing to do with catalyst...i uninstaled fglrx and now ubuntu uses mesa or radeonhd...i'm not shure....but i still get the same error.

---

### Post by moviemaniac on 2010-04-27
same error using the open source radeon driver on a 2600XT in 10.04

//edit: Filed a bugreport since it seems nobody has done so so far...
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/570646](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/570646)

---

