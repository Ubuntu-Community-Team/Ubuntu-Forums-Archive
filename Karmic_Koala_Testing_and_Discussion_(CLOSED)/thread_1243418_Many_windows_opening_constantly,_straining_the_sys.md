---
title: "Many windows opening constantly, straining the system, help?"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NCLI on 2009-08-18
A lot of windows are showing up in the panel, but they never appear on the screen! This hapens as soon as I boot :confused:

It was fine yesterday, maybe an update broke it?

Sometimes it looks like they all crash & dissapear, but then new ones just start spawning...

---

### Post by Regenweald on 2009-08-18
System tools>>Configuration Editor>>Apps>>Nautilus>>Preferences>> Turn 'Show Desktop' on

---

### Post by nyarnon on 2009-08-18
> **Regenweald said:**
> System tools>>Configuration Editor>>Apps>>Nautilus>>Preferences>> Turn 'Show Desktop' on

Why would he do that, he would lose his root window?

If it is what I think it is and it is Nautilus again he better edit /usr/share/applications/nautilus.desktop and set autorestart=false.

On the other hand I do not see anything pointing to the Nautilus spawn bug in his screenshots.

---

### Post by Regenweald on 2009-08-18
I did the autorestart=false fix and it worked for a few updates then reverted. i have no idea what you mean by root window. until this well documented bug is fixed, i simply show my desktop. Note the difference, show desktop set : off and on

---

### Post by Chronon on 2009-08-18
nevermind.

---

### Post by Regenweald on 2009-08-18
> **Chronon said:**
> nevermind.

Found it ? my connection just finished the shots...

---

### Post by NCLI on 2009-08-19
Yep, that was it.

Thanks for the advice, my desktop was useless!

---

