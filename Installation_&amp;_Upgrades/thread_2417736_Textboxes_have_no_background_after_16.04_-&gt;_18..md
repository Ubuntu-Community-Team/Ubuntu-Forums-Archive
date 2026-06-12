---
title: "Textboxes have no background after 16.04 -&gt; 18.04"
date: 2019-04-26
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2019-04-26
I have just (at work) had an update from 16.04LTS to 18.04LTS.

In "Gramps", a GTK application, pure text boxes (used for various parts of the program e.g. notes) do not write the background raster, so that the background, desktop (or whatever) shows through.

If I do a resize of such a box, all the successive text redraws (as the text reflows) overlay each other.

I have searched extensively for this, but found nobody else with the issue (and hence no "potted" cures).

Anything I can check/do?

EDIT: I was offered a choice between lightdm and gdm during the update, and chose lightdm.

  BugBear

---

### Post by bugbear6502 on 2019-04-26
Additional info.

I tried doing an ssh -Y from a friends machine, and it worked OK.

His machine was running gnome desktop manager, from 18.04LTS.

  BugBear

---

