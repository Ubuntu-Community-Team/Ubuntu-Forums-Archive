---
title: "Is there a standard about how apps should use the NA?"
date: 2008-05-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-05-21
Hi,

Some time ago I filed a bug against the gnome panel, asking for the NA to have a button to hide unused icons and avoid getting it overcrowded, just like windows. The answer was that the NA is intended for NOTIFICATIONS, and if it's crowded it's because apps don't use it properly. Which kinda makes sense.

There are lots of "background" apps that sit on the NA, though. Rhythmbox, Pidgin, Transmission are the first to come to mind. The way we do it is a mess, too. Some of them close when you press the X button, some are minimised to the NA. Some use the glide animation, some use zoom. Some bring the app to the front when you click the NA icon, some hide it. Some have a checkbox (not) to use the NA, which is nice since they "shouldn't" be using it in the first place... some dont.

Is there some kind of standard about this? Do the HIG say how these issues should be handled?

---

### Post by 23meg on 2008-05-21
There's the [fd.o System Tray Protocol Specification]("http://standards.freedesktop.org/systemtray-spec/systemtray-spec-0.2.html"), but it's pretty old and quite lax in specifying how NA items should behave. 

And here's the relevant heading from the GNOME HIG: [Using the Status Notification Area]("http://library.gnome.org/devel/hig-book/stable/desktop-notification-area.html.en")

---

