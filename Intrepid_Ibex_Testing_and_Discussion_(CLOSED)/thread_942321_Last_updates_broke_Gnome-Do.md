---
title: "Last updates broke Gnome-Do"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-09
Now it won't remember settings, I'm stuck with the default theme, and it doesn't remember my programs any more. 

Anyone else experience this after last update?

---

### Post by robzon on 2008-10-09
For me it just won't suggest my appliactions from the menu anymore. Annoying.

---

### Post by olavjunior on 2008-10-09
Yea, that's the real problem! Glad it's not just me! The mini layout work, but not the glass frame

---

### Post by bash on 2008-10-09
Got the same problem. Normally I use the Glass-frame layout, but since the last update Gnome-Do won't remember any changes in the settings I make. Anyone filed a bug yet?

Oh and does anyone know where Do saves it's configuration? So that I could at least change the default theme manually.

**Update**:

Found out what the problem is with not saving the layout. Basically Do saves the name of the layout in gconf. After last night update localisation was added. The problem is that Do only recognises the english layout names, but with the new version the layout names get saved in your local language. For example for me it had as a value "Glass Rahmen" (Glass frame in german). When I changed it back to "Glass Frame" and restarted Do, everything worked again.

So basically it should only be broken for everyone that uses a non english system.

---

