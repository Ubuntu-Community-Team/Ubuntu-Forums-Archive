---
title: "gconf-editor settings not recognised in 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by mdavies5 on 2012-10-19
In 12.04 I had a setting in gconf to set my form icons to the right of the form title bar I.E. /apps/metacity/general/button_layout = "menu:minimize,maximize,close".

All my icons now default to the left side in 12.10.
In gconf-editor it also features a red exclamation icon with text "This key has no schema".

Will this function move to myunity when it is available or has it been dropped?

---

### Post by grahammechanical on 2012-10-19
You will have to ask the myunity developer about myunity.

gconf-editor does not work in 12.10. You need to use dconf-editor, which may not be installed by default.

Regards.

---

