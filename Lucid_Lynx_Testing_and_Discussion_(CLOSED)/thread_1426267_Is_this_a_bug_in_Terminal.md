---
title: "Is this a bug in Terminal?"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2010-03-10
It seems that no-matter which theme I choose the Terminal window is always purple and uses the Ambiance theme (even if I select Radiance).

You can select terminal -> Change Profile -> Default to put it back to normal, but the next time you load Terminal it's back to purple.

The way things are changing right now I don't know whether this is a design decision or a bug...

---

### Post by tad1073 on 2010-03-10
no, you need to do alt+F2 gconf-editor, apps, gnome-terminal, global, and change default_profile

---

### Post by dino99 on 2010-03-10
> **Robin Nixon said:**
> It seems that no-matter which theme I choose the Terminal window is always purple and uses the Ambiance theme (even if I select Radiance).

You can select terminal -> Change Profile -> Default to put it back to normal, but the next time you load Terminal it's back to purple.

The way things are changing right now I don't know whether this is a design decision or a bug...

yes some confusing: Ambiance is the system theme (Lucid profile) and cant be removed, Radiance is the user's theme (your profile).

I've seen several comments about that and maybe a bug has been filled yet.

Oops, see post 2 above

---

### Post by Ichtyandr on 2010-03-10
Or in terminal go to Edit > Profiles > and there is an option "Profile used when launching a new terminal" choose "Default" or make your own

---

