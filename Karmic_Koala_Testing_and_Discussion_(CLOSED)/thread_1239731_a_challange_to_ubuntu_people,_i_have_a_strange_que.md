---
title: "a challange to ubuntu people, i have a strange question..."
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-08-13
i have a hp2133, 
with the via chipset and chrome9 graphics
basically nice hardware, bad graphics and no intel atom.

i have been using karmic since the first day, and it works well
but i cannot get the DRI to work, so no nice fast graphics, i have to use openchrome - which honestly, is choppy.. and theres no 3d.

so today - i went back to... HARDY.. yes, its a tad old, but it works.. 

i had to compile the broadcom STA stack myself, and i can only use the 2.6.24-16-generic kernel, because the drm/glx grahpics only work with this kernel..

now my question

how do i use karmic software versions ontop of hardy
can i just add the karmic reps, and install what i wish?
and just FORCE VERSION in synaptic of the kernel and xorg etc..?
is this possible?
will it work?

any ideas?

---

### Post by wayne_cat on 2009-08-13
You can not use Karmic packages on Hardy.

---

### Post by zekopeko on 2009-08-13
If you need newer versions of software try finding PPA's that have the hardy version. Just a word of caution: try using only the official ones from either Ubuntu developers or software developers of the software you want. Avoid those that are personal since they may pose a security risk.

---

### Post by puccaso on 2009-08-13
> **zekopeko said:**
> If you need newer versions of software try finding PPA's that have the hardy version. Just a word of caution: try using only the official ones from either Ubuntu developers or software developers of the software you want. Avoid those that are personal since they may pose a security risk.

ahh, not a bad idea
thank u.

---

### Post by ronacc on 2009-08-13
you could try local compiling the newer versions if you can't find .debs , but you will probably have to do a bunch of "adjusting" to the configure scripts , libs ,gcc version etc.

---

