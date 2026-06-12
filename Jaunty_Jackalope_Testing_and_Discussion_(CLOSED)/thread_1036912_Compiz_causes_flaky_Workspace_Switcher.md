---
title: "Compiz causes flaky Workspace Switcher"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-11
I have my workspace switcher set to 7 columns and 1 row.  When I use the mouse wheel to change desktops it causes the squares that represent the other open apps to show briefly on the wrong desktop then it corrects itself.  It is a real quick flash, but it catches the corner of my eyye most times I switch.

EDIT: It doesn't do this EVERY time, it depends on where the windows are in relation to the desktop I am currently viewing.  I have not found the pattern yet.

---

### Post by Gourgi on 2009-01-11
> **LordVeovis said:**
> I have my workspace switcher set to 7 columns and 1 row.  When I use the mouse wheel to change desktops it causes the squares that represent the other open apps to show briefly on the wrong desktop then it corrects itself.  It is a real quick flash, but it catches the corner of my eyye most times I switch.

EDIT: It doesn't do this EVERY time, it depends on where the windows are in relation to the desktop I am currently viewing.  I have not found the pattern yet.

could you try explaining it a little bit more ?
maybe using a screencast (gtk-recordmydesktop) or screenshot ?

---

### Post by LordVeovis on 2009-01-11
ok, I recorded it.  Where can I upload the vid too?

---

### Post by Gourgi on 2009-01-11
> **LordVeovis said:**
> ok, I recorded it.  Where can I upload the vid too?
if you have a google acount try :
[http://video.google.com/](http://video.google.com/)


or something similar (youtube mabe)

as for your bug , i can't reproduce it using the default 2 workspaces.

maybe it has something to do with your video card?

---

### Post by LordVeovis on 2009-01-11
I can't reproduce anymore... I will post again if it happens again.

---

### Post by Toe on 2009-01-11
Do you mean that within the workspaces applet the small representations of application windows get shown at incorrect places while you're switching workspaces?

If yes, the same thing happens on my Intrepid install. Usually under heavy CPU load.

Have you already filed a bug?

---

### Post by LordVeovis on 2009-01-12
> **Toe said:**
> Do you mean that within the workspaces applet the small representations of application windows get shown at incorrect places while you're switching workspaces?

If yes, the same thing happens on my Intrepid install. Usually under heavy CPU load.

Have you already filed a bug?

No I have not, and yes that is what I mean.  They appear on the desktop to the left or right for a few miliseconds then are back in place.

---

### Post by LordVeovis on 2009-01-12
I was able to reproduce again by having many different programs open across my 7 different desktops and then changing desktops by using the mouse wheel.

---

