---
title: "phantom floppy drive in karmic"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by klemperal on 2009-10-19
I installed the beta last night and now I'm having a strange issue.  My computer does not have a floppy drive, but, sure enough, one is showing up in the nautilus side pane, and in the other usual directories (computer, /media etc.).  I'm not really sure how to fix this at this point.  I tried deleting the floppy line from fstab, when I open up nautilus it is still there.  Any ideas?

---

### Post by egalvan on 2009-10-19
One possible answer: the floppy is not turned off in the BIOS.
Boot into the BIOS and make sure that the floppy is set as "not present",
 or whatever is close to that in your BIOS.

Another: it could be that Karmic **BETA** has left-over, phantom or extra code.
Wait for the final release, it may fix the problem.

Or take the lazy man's way out...
just ignore the non-existent floppy :)

---

