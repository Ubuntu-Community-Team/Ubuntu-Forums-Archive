---
title: "KDE apps aren't integrated into gnome"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-23
When I open Kalzium it looks just like KDE. I think I'm missing a package, anyone know what it is?

---

### Post by tchoklat on 2009-10-23
If u installed it through synaptic you should have all the necessary dependencies. Try apt-get remove <package> then reinstall it. I would do this as it wont hurt your system and may tell you what is wrong!

---

### Post by novafluxx on 2009-10-23
> **tchoklat said:**
> If u installed it through synaptic you should have all the necessary dependencies. Try apt-get remove <package> then reinstall it. I would do this as it wont hurt your system and may tell you what is wrong!

Actually, since that program is probably written in Qt, and Gnome is GTK based...and Gnome doesn't like KDE apps as much as KDE likes Gnome aps (as in trying to change their look & feel)...

---

### Post by AlphaLexman on 2009-10-23
Try this:
[INDENT]System, Preferences, Qt4 Settings
[INDENT]Appearance, GUI Style, Select GUI Style -> GTK+
[/INDENT][/INDENT]Will make KDE apps look like Gtk

---

### Post by Sashin on 2009-10-23
> **novafluxx said:**
> Actually, since that program is probably written in Qt, and Gnome is GTK based...and Gnome doesn't like KDE apps as much as KDE likes Gnome aps (as in trying to change their look & feel)...

What are you talking about? KDE apps used to integrate perfectly in gnome, much better than the other way round. But I think I uninstalled the package by accident. The integration one, and it doesn't automatically come about through installing with software center.

---

### Post by Sashin on 2009-10-23
> **AlphaLexman said:**
> Try this:
[INDENT]System, Preferences, Qt4 Settings
[INDENT]Appearance, GUI Style, Select GUI Style -> GTK+
[/INDENT][/INDENT]Will make KDE apps look like Gtk

Its not there.

---

### Post by FuturePilot on 2009-10-23
> **Sashin said:**
> Its not there.

Is qt4-qtconfig installed?

---

### Post by Sashin on 2009-10-23
After installing qt-config I can only customise the qtconfig window. Kalzium is oblivious to its effects.

---

### Post by Keyper7 on 2009-10-23
Are you sure you didn't install qt3-qtconfig by mistake?

That's strange, it should work. As far as I know, the GTK theming for Qt4 does not require any extra packages.

---

### Post by hikaricore on 2009-10-23
> **Sashin said:**
> After installing qt-config I can only customise the qtconfig window. Kalzium is oblivious to its effects.

You may also need to close and reopen any qt applications AFTER changing their visual settings.

---

### Post by AlphaLexman on 2009-10-23
Check synaptic, do you have 'python-qt4' installed?
I have Kubuntu and ubuntu both installed, so I don't know what a raw ubuntu has exactly.

---

### Post by Sashin on 2009-10-23
> **hikaricore said:**
> You may also need to close and reopen any qt applications AFTER changing their visual settings.

Not only did I do this, I actually restarted the computer.

---

