---
title: "gnome-volume-manager and sound-juicer missing?"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forumache on 2008-10-07
OK, not really missing, but they are not in main anymore. They are in universe.

I can see the reasoning behind removing sound-juicer: you can rip audio CDs with rhythmbox.

But gnome-volume-manager? This is supposed to start a program when you plug in your camera, or a DVD, whatever.

I tried to find some info on the net, but nothing was found. Could someone send my a link to some information about this?

Thanks.

---

### Post by wgrant on 2008-10-07
> **forumache said:**
> OK, not really missing, but they are not in main anymore. They are in universe.

I can see the reasoning behind removing sound-juicer: you can rip audio CDs with rhythmbox.

But gnome-volume-manager? This is supposed to start a program when you plug in your camera, or a DVD, whatever.

I tried to find some info on the net, but nothing was found. Could someone send my a link to some information about this?

Thanks.

Your reasoning for sound-juicer is correct. gnome-volume-manager is no longer necessary either - nautilus does the mounting now.

---

### Post by forumache on 2008-10-07
> **wgrant said:**
> Your reasoning for sound-juicer is correct. gnome-volume-manager is no longer necessary either - nautilus does the mounting now.

Thanks for answering so quickly.
I understand that nautilus does the mounting.
But running dpkg-query -L gnome-volume-manager I see that it also includes gnome-volume-properties (which is System|Preferences|Removable Drivers and Media)

I see that Nautilus has Edit|Preferences|Media, but it seems limited comparing with gnome-volume-properties:

no Digital Camera
no Digital Video Camera
no Web Camera
no Palm
no PocketPC
no Scanners, Printers, Mouse, Keyboard and Tablet

for all of the above you were able to assign an action to be executed at connection, using gnome-volume-properties.

OK, it is not a big problem. If this is the "new way" ;) I will remove sound-juicer and gnome-volume-manager from my Ubuntu

Thanks,
Dan

---

