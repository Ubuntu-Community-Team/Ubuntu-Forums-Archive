---
title: "Problems printing with Windows printer via Samba"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-04-15
I configured a "Windows Printer via Samba" using the System/Administration/Printing.  I left the option to "Prompt if user authentification is required".  

Printing from evince doesn't work -- it errors out with something like "unable to prompt for authentification" (can't reproduce again -- it errors out with "too many failed attempts").
Printing from acroread (uses lpr command) works, but the job sits in queue until I authenficate it by hand via System/Administration/Printing/MYPRINTER/View Print Queue.
Printing from Firefox used to work.  It no longer does, gives no error, the job doesn't even queue.

Any ideas?

---

### Post by mannheim on 2009-04-15
This looks like [bug #283811]("https://bugs.launchpad.net/ubuntu/+bug/283811"). See, in particular, [comment 37]("https://bugs.launchpad.net/ubuntu/+bug/283811/comments/37").

---

### Post by michael37 on 2009-04-15
> **mannheim said:**
> This looks like [bug #283811]("https://bugs.launchpad.net/ubuntu/+bug/283811"). See, in particular, [comment 37]("https://bugs.launchpad.net/ubuntu/+bug/283811/comments/37").

Indeed, looks quite similar.  Actually, my situation is closer to comment 5 since authentication is required for this printer.

I'll keep watching that bug...

---

