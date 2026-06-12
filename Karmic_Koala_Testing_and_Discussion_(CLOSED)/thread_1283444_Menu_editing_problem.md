---
title: "Menu editing problem"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-10-05
In the attached screenshot you will see that I have some items in my games menu which do not appear in the menu editor (all the ones after Nibbles). Any clues how I can edit them (e.g. move them or delete them? For example, I would like to move Globulation2 to the top of the menu.

---

### Post by Lampi on 2009-10-05
check out the xml desktop files in /usr/share/applications/ You should find a file called "globulation2.desktop" - edit this file - if it's not there search those desktop files content for globulation2.

---

### Post by ikisham on 2009-10-05
Open those folders (Strategy, Simulation and Kids) and see if they're inside.

---

### Post by ubername on 2009-10-05
> **ikisham said:**
> Open those folders (Strategy, Simulation and Kids) and see if they're inside.

Thanks. Found them in Strategy. Deleted them. Now they're gone from both places!. I will work it out though, thanks for the tip, I can't believe I didn't look there in the first place.

---

### Post by ikisham on 2009-10-05
You may go to /usr/share/applications and see if you find a .desktop file for it. Then you open the file and look if there's something that would make it go to the Strategy sub-category and then edit it.
That if you can't manage it through the menu editor.

---

