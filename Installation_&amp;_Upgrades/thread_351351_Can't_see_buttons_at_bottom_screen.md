---
title: "Can't see buttons at bottom screen"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Drummer4242 on 2007-02-01
This is my third time posting this issue. So far noone has responded. I am attempting to install Unbutu 6.06.1. I am unable to see the buttons at the bottom of the install screen so I'm stuck at the install screen. I'm using an All-In-Wonder 9600 powering a ViewSonic VA1912wb monitor which is a 19" widescreen. What can I do to be able to see the buttons? I would like to try Ubuntu along side Win XP.

---

### Post by jpeddicord on 2007-02-01
Is the window too big to fit on the screen? If so, you can probably move it by holding down <Alt> and dragging the window around. 

If the buttons just do not show up at all, try changing the system theme from System > Prefrences > Theme. That might reload all of the button images correctly.

Jacob

---

### Post by Drummer4242 on 2007-02-04
The problem is during the initial install and the window is full screen and not movable.

---

### Post by Oralloy on 2007-02-08
Hi Drummer,

I had a similar problem which I fixed by passing the following argument to the installer:

```
vga=771
```

I believe this is normally used for laptops however it worked for my 22" widescreen.

Hope this helps.

---

