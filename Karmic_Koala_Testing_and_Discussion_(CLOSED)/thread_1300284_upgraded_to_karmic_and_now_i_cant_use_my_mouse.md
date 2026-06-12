---
title: "upgraded to karmic and now i cant use my mouse"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jarrah-95 on 2009-10-24
this morning i upgraded to karmic and now i cannot use the touchpad (the cousor is there but it wont move. i tryed to post here this morning via the terminal (i can still use the keybord and have set shortcuts to the terminal aswell as other things) but w3m whouldent let me post here it just reloaded the new thread page whenever i press submit new thered. anyway back to the main problem. how can i fix my touch pad from the terminal so i can use ubuntu properly
now i see why i forced my self to learn a little bit about the terminal.
thanks

---

### Post by CommonClone on 2009-10-25
I am having the same problem with my laptop.  I would appreciate some help.

---

### Post by CommonClone on 2009-10-27
Okay, I fixed the problem.  For some reason, grub was not loading the updated kernel.  I went ahead and updated to grub 2, and in the process the new kernel was loaded into the grub menu.  Also, the new kernel fixed my sound problems.

I am guessing that the numerous threads concerning broken audio and touchpad issues are due to this problem.  Perhaps a sticky thread should be written.

---

