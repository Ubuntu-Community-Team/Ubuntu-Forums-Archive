---
title: "Workspace switcher annoyance"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by billgoldberg on 2009-04-19
A little text balloon keeps popping up whne switching workspaces.

I don't know why they did it, it just annoys me.

I'm guessing there is no way to disable that?

---

### Post by Lorag on 2009-04-19
Try gconf-editor:
/apps/panel/global>Tooltips_enabled false

Good luck

---

### Post by billgoldberg on 2009-04-19
> **Lorag said:**
> Try gconf-editor:
/apps/panel/global>Tooltips_enabled false

Good luck

Thanks, that did it.

---

