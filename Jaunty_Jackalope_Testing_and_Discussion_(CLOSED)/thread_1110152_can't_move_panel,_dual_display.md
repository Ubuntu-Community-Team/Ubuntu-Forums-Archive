---
title: "can't move panel, dual display"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by djxstream on 2009-03-29
So i did a clean install w/ the Jaunty Beta (64 bit) from my previous install of 32 bit Intrepid.  

On my previous I managed to drag my bottom panel onto the 2nd screen.

Now with 64 bit Jaunty i used the restricted drivers and setup my twinview working properly. however I can't seem to drag the bottom panel from one screen to the other? 

I tried editing the screen number in gconf-editor but it just reverted back to zero.  any advice?

thanks

---

### Post by Bou on 2009-03-29
Hm, I think to remember something about panels not being movable in gnome 2.26, or you at least having to do some mumbo-jumbo to move them.

---

### Post by Darkshade on 2009-03-29
Option 1: Open gconf-editor, go to apps -> panel -> toplevels and select the panel you want to move. Change the value of "monitor" (not screen) from 0 to 1 and you're done.

or

Option 2: Right-click the panel, select properties, uncheck "expand" and drag it clicking on the side arrows/buttons to the other screen, then check "expand" again.

There might be another way but I only found these 2 while going trough the same troubles as you.

---

### Post by zekopeko on 2009-03-29
...or press and hold ALT while draging the panel

---

### Post by Naddiseo on 2009-03-29
Here's the bugzilla for this: [http://bugzilla.gnome.org/show_bug.cgi?id=562944](http://bugzilla.gnome.org/show_bug.cgi?id=562944)

---

### Post by djxstream on 2009-03-29
holding ALT did the trick thank youuuuuuuuuuuu

---

### Post by Darkshade on 2009-03-29
> **zekopeko said:**
> ...or press and hold ALT while draging the panel

Last time that worked for me was in Intrepid...

---

### Post by Mr. Picklesworth on 2009-03-29
> **djxstream said:**
> So i did a clean install w/ the Jaunty Beta (64 bit) from my previous install of 32 bit Intrepid.  

On my previous I managed to drag my bottom panel onto the 2nd screen.

Now with 64 bit Jaunty i used the restricted drivers and setup my twinview working properly. however I can't seem to drag the bottom panel from one screen to the other? 

I tried editing the screen number in gconf-editor but it just reverted back to zero.  any advice?

thanks

Just hold down Alt and drag to move them. It makes a bit more sense; just like dragging any other windows :)

Edit:
Ack! Not reading the whole thread for the lose!

Anyway, I for one like this change. Locking / unlocking panels was a horrible kludgey workaround to the issue of people dragging the things by accident, and changing any other setting needs the context menu so there's really no point wasting that gesture for moving the panel.

---

