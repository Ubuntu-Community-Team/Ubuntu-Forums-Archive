---
title: "Major problem after update"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by The Frenchman on 2013-09-19
Hadn't used my laptop for a while so logged on and did updates.Within a few minutes lost use of several letters on the keyboard.Sadly two of which are used in my pasword.I can log on to my normal account using onscreen keyboard but all I get is desktop showing my folders,cant get dash or settings to log off or exit.Obviously can access guest but can't autherise anything because of inability to use password.Any hints as to what to do next?

---

### Post by Jonathan Precise on 2013-09-19
Please post your version of ubuntu, as commands may vary between them.

Example: Ubuntu 11.04 and earlier:

Log out dialog: gnome-session-save --logout-dialog
Shut down dialog: gnome-session-save --shutdown-dialog
Unity (panel, dash/launchers, etc.): No idea!

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Ubuntu 12.10 and newer:

Log out dialog: gnome-session-quit
Shut down dialog: gnome-session-quit --power-off
Unity (panel, dash/launchers, etc.): unity

---

### Post by The Frenchman on 2013-09-19
Sorry 12.04LTS

---

### Post by The Frenchman on 2013-09-19
I should add that in my account screen nothing at all works.Just shows the desktop wallpaper with folders showing and nothing at all else.

---

### Post by Jonathan Precise on 2013-09-19
> **The Frenchman said:**
> I should add that in my account screen nothing at all works.Just shows the desktop wallpaper with folders showing and nothing at all else.

I'm not too familiar with ubuntu 12.04 LTS (have not used it in a while). Press Ctrl. + ALT. + T to bring up a terminal. Then run:

```
unity
```

If you do not see borders on the windows, then use:

```
metacity --replace
```

for "Ubuntu 2D" or:

```
compiz --replace
```

for full Ubuntu, then run unity again.

If it works, then open a new tab (Shift + Ctrl. + T) and type in:

```
gnome-session-properties
```

And add 2 programs:
[QUOTE=First program]Name: Borders
Command: ```
metacity --replace
``` or ```
compiz --replace
```[/QUOTE]

[QUOTE=Second program]Name: Borders
Command: ```
unity
```[/QUOTE]

Then mark as solved by going to thread tools.

---

### Post by The Frenchman on 2013-09-25
Thanks Jonathan I managed to open a terminal ran unity then everthing looked back to normal,but when I logged in the next time it had reverted.Ran unity again and it all came back,but the fix only seems to work each log in.

---

### Post by The Frenchman on 2013-09-27
all qui[COLOR=#000000]et [/COLOR]:D

---

### Post by Jonathan Precise on 2013-09-27
> **Jonathan Precise said:**
> If it works, then open a new tab (Shift + Ctrl. + T) and type in:

```
gnome-session-properties
```

And add 2 programs:




Then mark as solved by going to thread tools.

Try that to make it permanent.

[HR][/HR]

> All quiet :D

Sorry, I have been away for a while.

---

### Post by The Frenchman on 2013-10-08
Sorry Jonathan.I should have guessed you might be away.The fix you gave me works but only on a temp basis.everthing seems fine then next logon back to square one.looks like a full reinstall or upgrade to latest version might be a way forwards

---

