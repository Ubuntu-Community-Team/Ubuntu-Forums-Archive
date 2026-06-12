---
title: "Wine Uninstallation Trouble"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Rostir on 2009-12-30
I'm using the latest version of Ubuntu, GNOME. I installed iTunes using Wine, and the result was extremely buggy. Every time I go to the Wine uninstallation window, and click, Remove iTunes, it re-installs itself rather than removing itself, it's as if the uninstallation .exe for iTunes doesn't exist.

---

### Post by ajgreeny on 2009-12-30
Have a look in your home folder for the ~/.wine folder and in that you will find a folder for the itunes application, which you can just delete, if you want to.  If you have no other applications in wine and don't need it any more, delete the whole ~/.wine folder after uninstalling wine itself.  Everything will then be gone.

---

### Post by Rostir on 2009-12-30
I deleted the entire .wine folder, but Wine still shows up as a selection in the Applications menu, how can I get rid of this?

---

### Post by ajgreeny on 2009-12-30
Right click on the menu button or bar and choose Edit Menu.  You can delete the entry from there.

---

