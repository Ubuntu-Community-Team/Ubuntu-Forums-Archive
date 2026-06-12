---
title: "gparted taking hours... need help now!!!!"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by dan171717 on 2007-11-12
right i wacked in a gutsy ship it cd into a computer and resised an ntfs partion in gparted


i though it would take seconds like it has done for me before

but i was wrong


it has take two hours to read the ntfs partion and is now copying it to god knows where


this is not my computer so must not f**k up

neep help now


will it erase the partion or will it all be ok

---

### Post by dan171717 on 2007-11-12
please please please help me i need to know what to do now!!!!

---

### Post by Surkow on 2007-11-12
It's not likely you will lose your data. What I understand is that GParted uses a program called "ntfsresize" to resize your ntfs partition. If you would use ntfsresize directly it would report problems if anything would go wrong.

---

### Post by dan171717 on 2007-11-12
but does this normaly take forever on a comp twice the spped as one that can do it in seconds??

---

### Post by Surkow on 2007-11-12
> **dan171717 said:**
> but does this normaly take forever on a comp twice the spped as one that can do it in seconds??

Does the program (GParted) still respond? Perhaps it's not even busy resizing. Try to see if you are allowed to mount the drive (if you can't - GParted it busy with it).

---

### Post by dan171717 on 2007-11-12
> **dan171717 said:**
> but does this normaly take forever on a comp twice the spped as one that can do it in seconds??
it is now spending the next hour "copying" blank data

i never asked it to copy anything i told it to resise not copy resize


so why was it reading and copying

plz help this is making me :confused:

---

### Post by Surkow on 2007-11-12
The best solution is to wait till it finishes. This way you can be sure your data is still ok. If it's taking too long you can kill the process. After that you can check if anythings wrong.

---

### Post by dan171717 on 2007-11-12
> **Surkow said:**
> Does the program (GParted) still respond? Perhaps it's not even busy resizing. Try to see if you are allowed to mount the drive (if you can't - GParted it busy with it).
oh didnt see that


it is definatly respoding

it is moving allong but just verry slowly

---

### Post by dyous87 on 2007-11-12
if it is responding i would wait it out. you don't wana kill the process and then truly  fragment your data. let us know what happens.

---

