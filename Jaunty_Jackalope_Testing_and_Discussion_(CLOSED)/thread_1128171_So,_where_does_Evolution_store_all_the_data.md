---
title: "So, where does Evolution store all the data?"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-04-17
So I downloaded and installed the RC today, and tried to start afresh by using a new /home. I copied the config folders I thought I would need (.purple, .tomboy...) but even though I also copied .evolution, Evo now shows me the first launch wizard.

So the question is, what folders do I have to copy to be able to use my old evolution data?

---

### Post by kurros on 2009-04-17
The mail data is in ~/.evolution but the settings, account information, etc is stored in gconf, gnome-keyring, etc. You can migrate the gconf tree from under ~/.gconf/apps/evolution

---

### Post by Bou on 2009-04-17
Thanks a lot kurros. Is there really a logic behind that, though? Why not store everything in a place?

---

### Post by MaX on 2009-04-17
> **Bou said:**
> Thanks a lot kurros. Is there really a logic behind that, though? Why not store everything in a place?

Look for a bug in bugzilla or post one.

---

