---
title: "OpenOffice under Koala - texts in menus and dialogs corrupted"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by helenuh on 2010-01-11
I installed Koala a few days ago, including newest OpenOffice. Worked fine.

Suddenly yesterday all system-generated texts (menus, dialogs) got replaced by hyphen-like characters. Otherwise the software seems to work normally. Text I enter myself is displayed normally, as are icons and such.

The problem affects all OpenOffice applications but no other software (Kile, Evidence, GIMP etc work normally).

I tried to purge all software packages (including config files) that have "openoffice" in their description, and reinstall. I have done it both using apt and using synaptic. Doesn't help.

Looks as if OpenOffice can't find the font it wants to use to generate texts. Maybe it has become configured to some non-latin alphabet for which I don't have the font or something like that? Maybe I didn't manage to purge and reinstall OpenOffice entirely? Maybe the problem is in some other package on which OpenOffice relies?

---

### Post by SecretCode on 2010-01-11
Can you go to Tools > Options...
[SIZE="1"]In Writer, Tools is the 7th main menu item and Options is the last item in the tools menu[/SIZE] :)

Do you get legible fonts in the options dialogue?

What is set under OpenOffice.org > Fonts?

---

### Post by helenuh on 2010-01-11
Thanks!

No, options/fonts is the same as the rest of the menu system. [IMG]https://sites.google.com/site/helenehthygesen/images/Screenshot-1.png[/IMG]

How do I find OpenOffice.org > fonts ?

---

### Post by SecretCode on 2010-01-11
> **helenuh said:**
> How do I find OpenOffice.org > fonts ?That is the options page you posted ... not looking good!

Can you post the output of
```
sudo aptitude search ~iopenoffice
sudo aptitude search ttf-dejavu ttf-liberation ttf-mscorefonts-installer
```

---

### Post by Hagar Delest on 2010-01-11
See that thread, several fixes (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by helenuh on 2010-01-11
thanks, everyone for helping. changing the desktop application font from sans to arial solved the issue :)

---

