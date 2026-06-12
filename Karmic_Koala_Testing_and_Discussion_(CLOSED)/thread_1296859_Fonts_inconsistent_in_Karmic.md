---
title: "Fonts inconsistent in Karmic"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by UCAP on 2009-10-21
Since upgrading to Karmic yesterday my fonts are displayed inconsistently. It is hard to explain what I mean, that's why I added a screenshot.

Have a look at how the menu entries (File, Edit etc.) for instance are displayed differently in Synaptic and Nautilus.

Does anyone know what I can do to get rid of this problem?

---

### Post by psyke83 on 2009-10-21
> **UCAP said:**
> Since upgrading to Karmic yesterday my fonts are displayed inconsistently. It is hard to explain what I mean, that's why I added a screenshot.

Have a look at how the menu entries (File, Edit etc.) for instance are displayed differently in Synaptic and Nautilus.

Does anyone know what I can do to get rid of this problem?

The thumbnail is too small to see any detail in your screenshot.

---

### Post by UCAP on 2009-10-21
@psyke83: Thanks. I have added a better screenshot.

---

### Post by TrueTom on 2009-10-21
Try running Nautilus with [FONT="Courier New"]gksudo[/FONT] and check if it has the same font sizes as Synaptic or normal Nautilus.

---

### Post by UCAP on 2009-10-21
Running nautilus (and other programmes that showed this font behaviour for that matter) with gksudo does indeed make sure that the fonts look the same as in Synaptic.

How can I make this permanent (without gksudo)?

---

### Post by Bluppie on 2009-10-21
I have look at my own system but I kan not see any difference's in my fonds. So I think your fonds are an little mixt up.
Is in scim the fond type on default?

---

### Post by Tibuda on 2009-10-21
I think this happens because the font you are using is only available for you user (in ~/.fonts), so when you run an app as root (like synaptic) it will not use that font. The same thing happens with GTK+ themes.

---

### Post by johoe on 2009-10-21
run

sudo gnome-appearance-properties

then do the same theme/font etc settings as root...

I prefer to have it different, so I can see immediately that a certain program is executed as root...

 johoe

---

### Post by UCAP on 2009-10-21
Thank you all for your help.

The solution turned out to be quite simple. Deleting the ~/.fonts.conf file did the trick. When I logged out and back in again the fonts were back to normal.

---

