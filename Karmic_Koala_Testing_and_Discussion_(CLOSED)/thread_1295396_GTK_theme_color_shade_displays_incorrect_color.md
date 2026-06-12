---
title: "GTK theme color shade displays incorrect color"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Brandon Williams on 2009-10-19
I installed Friday's (10/16/2009) "current" build for lpia to a Dell mini 10v. All packages are up-to-date, except for transmission-gtk, which can't be updated off of the current repo contents.

All GTK themes that use the shade function to darken colors are displaying bad colors for the associated GUI elements. For example, shiki-brave, which should display a blue background behind the currently selected menu item is displaying pink instead. If I calculate the shaded color by hand and replace all use of shade with a static value, the theme appears as expected.

I have tested all GTK themes currently installed on my system (including  Industrial, Mist, Albatross, Crux, and Clearlooks) and found that there are elements of each one that display an incorrect color. It's most apparent with shiki-brave, since it has the most extensive use of the shade function.

Has anyone else seen this problem? And whether or not you've seen it, can anyone select an appropriate project for me to assign the bug to in launchpad?

---

