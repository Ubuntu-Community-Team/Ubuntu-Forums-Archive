---
title: "Why isn't there an option in display to choose the main screen?"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-27
everytime i enable a second screen like my tv it's automaticly identified it as the main screen and i can't do nothing about it.

thanks in advance.

---

### Post by chrisccoulson on 2010-02-27
I've wondered the same thing. It's supported by gnome-desktop, as you can edit ~/.config/monitors.xml, and change "<primary>no</primary>" to "<primary>yes</primary>" for the monitor in the configuration stanza you're using. If you do that, your desired monitor will be primary next time you log in.

I'll see if this is exposed in the gnome-desktop API. If it is, it would be trivial to add the option to the UI.

---

### Post by ssam on 2010-02-27
if you want the gnome-panel on a different screen then just hold down alt and drag them.

---

### Post by aviramof on 2010-02-27
> **chrisccoulson said:**
> I've wondered the same thing. It's supported by gnome-desktop, as you can edit ~/.config/monitors.xml, and change "<primary>no</primary>" to "<primary>yes</primary>" for the monitor in the configuration stanza you're using. If you do that, your desired monitor will be primary next time you log in.
 
I'll see if this is exposed in the gnome-desktop API. If it is, it would be trivial to add the option to the UI.
 
it would be great if it's possible to add to the UI.

---

### Post by ronacc on 2010-02-27
A switch in "display"  would be very helpful , I'll try chrisccoulson's method later , I have my big screen tv on the vga output of my video card and my ws monitor on the dvi and have to go through all kinds of monkey motion to get GDM to put my desktop on the monitor and use the tv as secondary.

---

### Post by aviramof on 2010-03-04
any news about adding this option?

thanks in advance.

---

