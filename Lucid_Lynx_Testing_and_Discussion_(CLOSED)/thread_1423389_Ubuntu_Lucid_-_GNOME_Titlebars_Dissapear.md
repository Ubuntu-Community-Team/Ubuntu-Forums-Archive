---
title: "Ubuntu Lucid - GNOME Titlebars Dissapear"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rinoshea on 2010-03-06
I'm testing Ubuntu Lucid Alpha 3, and enjoying the experience. 

_I've encountered an odd bug and I'm not sure where or how I should report it._ It's not the type where I get a bug report that I could submit.

**The issue is the disappearance of the GNOME window titlebars from all the windows, and the loss of the ability to open, close, or switch focus to any window.** It can occur at any time, and I have not found any particular thing that causes it.

Restarting Gnome fixes the issue (service gdm stop && startx), but all of my programs are closed in doing so.

[B]My question is: 
[/B]
[LIST=1]
[*]**Is there a way to restart Gnome without exiting all programs (or at least without Gnome not realizing that they're still running in the background)?**
[*]**Where and how should I submit this bug?**
[/LIST]
Thanks for helping me help the Ubuntu devs.

---

### Post by gjoellee on 2010-03-06
> **rinoshea said:**
> I'm testing Ubuntu Lucid Alpha 3, and enjoying the experience. 

_I've encountered an odd bug and I'm not sure where or how I should report it._ It's not the type where I get a bug report that I could submit.

**The issue is the disappearance of the GNOME window titlebars from all the windows, and the loss of the ability to open, close, or switch focus to any window.** It can occur at any time, and I have not found any particular thing that causes it.

Restarting Gnome fixes the issue (service gdm stop && startx), but all of my programs are closed in doing so.

[B]My question is: 
[/B]
[LIST=1]
[*]**Is there a way to restart Gnome without exiting all programs (or at least without Gnome not realizing that they're still running in the background)?**
[*]**Where and how should I submit this bug?**
[/LIST]
Thanks for helping me help the Ubuntu devs.

The window borders (as I assume you are referring to) are called "metacity". Simply run ```
metacity
``` in the terminal or in the ALT + F2 (run dialog). Run the code in the terminal if it fails. The error should be listed int he output.

---

### Post by rinoshea on 2010-03-07
Thanks. Should have thought of that myself....been using Ubuntu for about a year. 

Thanks for the input -- will run it if the problem persists.

Any ideas for submitting a bug that is this general in nature?

---

### Post by jeSah8ci on 2010-03-17
I've experienced this consistently -- always on startup -- since I upgraded from Karmic to Lucid.

My fix was to click on System / Appearance, then click the Visual Effects tab and click on Normal. After searching for drivers, the window borders reappear.

I'll try restarting my system and running metacity, like gjoelle said.

Since I experience this consistently, is there something I can do to help resolve this issue?

What package should I report this bug into?

---

### Post by rinoshea on 2010-03-24
> **rolandog said:**
> I've experienced this consistently -- always on startup -- since I upgraded from Karmic to Lucid.

My fix was to click on System / Appearance, then click the Visual Effects tab and click on Normal. After searching for drivers, the window borders reappear.

I'll try restarting my system and running metacity, like gjoelle said.

Since I experience this consistently, is there something I can do to help resolve this issue?

What package should I report this bug into?


Our problems seem to be virtually identical, except that this problem persists for me even when desktop effects are enabled.

---

### Post by lidex on 2010-03-24
If you're using compiz in gnome I'm thinking the command should be ```
gtk-window-decorator
``` If you have ccsm installed check the command field in Window Decorator plugin. If that value = ```
/usr/bin/compiz-decorator
``` then the script runs at startup and should choose the correct decorator.

---

