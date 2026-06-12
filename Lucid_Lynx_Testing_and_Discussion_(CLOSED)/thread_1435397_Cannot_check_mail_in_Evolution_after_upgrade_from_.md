---
title: "Cannot check mail in Evolution after upgrade from Karmic"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jonie on 2010-03-21
In fact I can, but only if I start Evolution from Applications menu. If I click the envelope icon, it starts evolution --component=mail and hangs while checking mail

---

### Post by sigixv on 2010-03-25
+1

---

### Post by grandtoubab on 2010-03-25
No problem for me.
Did you check if Evolution is still your prefered mail application??
System-> Preferences ->

---

### Post by sigixv on 2010-03-25
jup, it is selected there

---

### Post by sigixv on 2010-03-26
edit: evolution hangs after a while even with the method of using the menu to start it

---

### Post by philinux on 2010-03-26
@all

Start it from the terminal, see if any errors spit out.

```
evolution --component=mail
```

---

### Post by sigixv on 2010-03-26
```
wim@toshiba:~$ evolution --component=mail
** (evolution:1396): DEBUG: mailto URL command: evolution %s
** (evolution:1396): DEBUG: mailto URL program: evolution

```
I'll leave it open for a few hours, maybe something will show up when it starts to hang.

---

### Post by sigixv on 2010-03-26
```
Segmentatiefout (geheugendump gemaakt)
```Translates as something like: "Segmentational error. (Performed memory dump)"

This time it didn't hang (or not that i saw happening, it was minimized) and i get a box explaining the error:

Translated:
[B][I]Application Error
[/I][/B][I]We apologize, the program "evolution" has been closed unsuspectedly.
If you were doing nothing confidential, you might be able to improve the application by reporting the problem.

[/I]And then i click to report the button.

[I][B]Problem in evolution
[/B]The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

base-files, cpp-4.4, gcc-4.4-base, libaspell15, libbluetooth3, libcups2, libdbusmenu-glib1, libdbusmenu-gtk1, libgail18, libgcc1, libglib2.0-0, libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common, libgudev-1.0-0, libstdc++6, libudev0, sensible-utils, shared-mime-info, udev

[/I]
This is the second time i get this box, both times i was unable to report.
What mostly happens is: auto mailchecking is busy, but doesn't complete. When clicking send/recieve it will tell me whats happening with my 2 mailboxes but it doesn't seem to download. (the number of new mails in the mailbox however is correctly displayed). Apparently if you wait even longer, evolution implodes on itself...
Force quitting renders evolution unusable: the process keeps running and restarting is impossible. When logging out/restarting i am prompted that 1 or 2 processes of evolution are still running.


Edit: for what the packages is concerned, i did a fresh install of lucid with an evolution backup created in karmic. Lucid is fully updated with the update manager.

---

