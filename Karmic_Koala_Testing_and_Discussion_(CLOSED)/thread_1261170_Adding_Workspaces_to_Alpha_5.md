---
title: "Adding Workspaces to Alpha 5"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-09-08
When I right click on the Workspace Switcher and select Preferences all I get is a window saying:

Columns: 0
Rows: 0

Changing any of those values doesn't do anything, so I'm wondering how/if I can add more Workspaces under this version of Ubuntu...?

---

### Post by steeleyuk on 2009-09-08
Its a known bug. Not seen any workarounds though...

Edit: Actually, you can add the workspaces through gconf > /apps/metacity/general/num_workspaces

---

### Post by zika on 2009-09-08
gconf-editor->apps->metacity->general->num_workspaces =4 (for example) ...

---

### Post by Robin Nixon on 2009-09-08
Thanks for that info both of you!

[Edit below]

FYI - I just had reason to disable the Nvidia proprietary driver and after that proper Workspace Switcher preferences window returned. But you still can't add Workspaces.

---

