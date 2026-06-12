---
title: "Ubuntu will not install"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Dalto11 on 2008-06-05
So I downloaded Ubuntu 8.04's image file and burnt it to a disc. I run it, select install, it loads it all up. I go through it till step 3. After I click forward on step 3 it runs the progress bar to load the partitioner and just hangs. I can still click on stuff and what not, but setup never goes any farther. The only problem I can for see causing it is the two buffer errors it hits, but when I run detect CD for problems it shows them, continues to to scan and says their are NO problems. Any ideas as to why the install won't run?

The buffer errors given during Ubuntu's startup are:

[ 234.794402] Buffer I/O error on device fd0, logical block 0
[ 272.857315] Buffer I/O error on device fd0, logical block 0


(If this is in the wrong section, forgive me I am new.)

---

### Post by Partyboi2 on 2008-06-05
try disabling the floppy and floppy drive controller in bios if you are able to. Another thing you could try is adding nofloppy as a boot option. So at the main menu press F6 and at the end of the line add ```
nofloppy
``` then press enter. if nofloppy does not work you could also try
```
all_generic_ide
```

---

### Post by erginemr on 2008-06-05
And a similar workaround is to disable the floppy drive from BIOS...

---

### Post by Dalto11 on 2008-06-05
Still hitting buffer I/O error on device fd0, logical block 0.
Any other suggestions?

---

### Post by Partyboi2 on 2008-06-05
Have you tried to install with the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/hardy/")?

---

### Post by Dalto11 on 2008-06-05
Downloading, gonning to try it, I hope it works.

EDIT:

Nope, hangs at the same part. The Partitioner's progress bar comes up, goes all the way, disappears and it stays at step 3.

---

### Post by Partyboi2 on 2008-06-06
What are your system specs?

---

### Post by Tek-Noir on 2008-06-06
Im getting the same problem, it was all working fine before. Did a clean install and now having loads of problems

---

### Post by Tomatz on 2008-06-06
Try putting a blank floppy into the floppy drive or you could try physically disconnecting it. If you still cant get past the error try wubi:

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Tek-Noir on 2008-06-06
Tried the wubi it didnt work and i dont have a floppy attached.

Im trying it at the minute using the safe graphical install, its got me further than last time. Keeping fingers crossed at the minute. Ill let you know how i get on.

---

### Post by Tek-Noir on 2008-06-06
Yep the safe graphical install seemed to work fine for me, give that a go.

---

### Post by Dalto11 on 2008-06-06
> **Partyboi2 said:**
> What are your system specs?

2Ghz processor
128mb GeForce FX 5200
256mb of RAM (might be the problem)



EDIT:

Tried graphical safe mode, the screen just goes black and my moniter goes into stand-by. I'll try the blank floppy trick

---

