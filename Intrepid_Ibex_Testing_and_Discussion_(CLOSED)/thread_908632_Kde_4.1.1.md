---
title: "Kde 4.1.1"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-02
I see that KDE 4.1.1 packages have started hitting the repositories. Cool! I'm waiting for all the packages to be uploaded before I reboot, I want to make sure I get the full experience and see if the bugs I reported have been fixed. I'm sure it's only a matter of time before the rest of the packages hit. How has it been so far for the rest of you?

---

### Post by beartard on 2008-09-02
So far the same fsck problems on boot with kernel 2.6.27-2 and wireless manager not working.  Other than working around those, everything seems to be fine.

---

### Post by jlacroix on 2008-09-02
I'm hoping at least the trash plasmoid works now. :(

I'll find out when I reboot but I am waiting to make sure I got all the packages.

Juk needs to be updated, I hope the bugs are fixed in that too, it's barely usable for me in its current state.

---

### Post by beartard on 2008-09-02
Does the trash plasmoid not work?  I've noticed since kde4.0 came out, the icon doesn't change to show if it's empty or not, but it seems to work otherwise.  When emptying the trash in dolphin (which I still really don't care for as a file manager) it even plays a noise to let you know it's deleting.

---

### Post by jlacroix on 2008-09-02
> **beartard said:**
> Does the trash plasmoid not work?  I've noticed since kde4.0 came out, the icon doesn't change to show if it's empty or not, but it seems to work otherwise.  When emptying the trash in dolphin (which I still really don't care for as a file manager) it even plays a noise to let you know it's deleting.

Nope! Still broken. It works if you empty it in Dolphin though.

I wonder though if its now an Ubuntu bug, because in Hardy if you emptied the trash from the widget, it would empty the trash and just not update the icon.

Now, in Intrepid, it doesn't do either.

---

### Post by jlacroix on 2008-09-02
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+bug/264163](https://bugs.launchpad.net/ubuntu/+bug/264163)

I already filed a similar bug report with KDE, but this particular problem is with Intrepid, because at least with Hardy it would still empty the trash.

---

