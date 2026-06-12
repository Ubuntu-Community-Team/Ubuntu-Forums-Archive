---
title: "&quot;Borders&quot; on the desktop due to Nautilus"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blazemore on 2010-02-15
On my current Lucid system, with some themes (particularly eGTK/elementary) Nautilus draws solid-coloured stripes down the left and right of the desktop. If I use xkill to get rid of Nautilus they disappear, but then I obviously lose my desktop icons.
Why is this?

I'll attach a screenshot when I get home.

---

### Post by dmitrijledkov on 2010-02-15
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263")

1px or more depending on the theme? =)

---

### Post by blazemore on 2010-02-15
Here's a screenshot. As a workaround, can I prevent Nautilus from drawing desktop icons?
EDIT: Got it, in gconf-editor, set /apps/nautilus/preferences/show_desktop to False

---

### Post by uBeer on 2010-02-15
What you can do to start nautilus again (so it doesn't display the light border) is executing
```
nautilus -q
```
It kills and restarts nautilus so you'll still have your desktop icons.

---

### Post by Russel_Winder on 2010-03-04
I have just installed Lucid and was very annoyed by these "desktop borders".  Thanks for the tip about "nautilus -q" which works well.  I wonder though if this should be considered a bug:  is there a bug report for this so that the default is not to have them?

---

### Post by Atermoon on 2010-03-04
> **Russel_Winder said:**
> I have just installed Lucid and was very annoyed by these "desktop borders".  Thanks for the tip about "nautilus -q" which works well.  I wonder though if this should be considered a bug:  is there a bug report for this so that the default is not to have them?

"nautilus-q" is only a temporary fix (and I mean until you add/move/rename a file on your desktop, change a theme, etc).
And yes, it is a bug and it has been reported. The link is in the 2nd post.

---

### Post by cyberkilla on 2010-03-04
> **blazemore said:**
> Here's a screenshot. As a workaround, can I prevent Nautilus from drawing desktop icons?
EDIT: Got it, in gconf-editor, set /apps/nautilus/preferences/show_desktop to False

Nice desktop:O

---

### Post by Uncle Spellbinder on 2010-03-04
> **uBeer said:**
> What you can do to start nautilus again (so it doesn't display the light border) is executing
```
nautilus -q
```
It kills and restarts nautilus so you'll still have your desktop icons.
Yep. Works like a charm. Except if you rename a desktop file or change a theme or change a wallpaper or sneeze, it comes back. Your forever opening terminal and executing *nautilus -q*.

---

### Post by ffi on 2010-03-04
[https://bugzilla.gnome.org/show_bug.cgi?id=605704](https://bugzilla.gnome.org/show_bug.cgi?id=605704)

---

### Post by t.rei on 2010-03-05
bugs me too. Am still looking for a fix.

Idea being followed atm: maybe some attribute like "thickness" in gtkrc files is responsible for this. Maybe, just maybe one can change that one attribute for nautilus?

---

