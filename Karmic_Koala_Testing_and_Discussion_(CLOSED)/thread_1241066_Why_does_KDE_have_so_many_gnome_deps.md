---
title: "Why does KDE have so many gnome deps?"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-08-15
My main OS is Arch with KDE but I have a spare partition for testing development releases. I installed alpha 4 yesterday (normal ubuntu version) to see what the new gnome beta was like (disappointing as usual) then installed kubuntu-desktop and went ahead and removed anything to do with gnome & gtk  but couldnt believe how many gnome/gtk dependencies that KDE has on ubuntu. A few examples:
**app-install-data**
**gconf2**
**libgconf2-4**
**gconf2-common**
**gnome-mime-data**
[B]libgnomevfs2-0
[/B]**libgnomevfs2-common**
[B]libpolkit-gnome0
policykit-gnome
python-gobject
libavahi-glib
libahavi-ui0
[/B]**libgtk2.0-0**(wants to remove amarok aswell)
[B]libgtk2.0-common
libsexy2
[/B]all want to remove k3b, kpackagekit and update-notifier-kde
**libXML **(GNOME XML library)
wants to remove pretty much every kde program

Theres probably loads more but they were the only ones I found straight away, on arch I have a full KDE desktop without anything gnome/gtk installed

---

### Post by Bachstelze on 2009-08-15
What package did you install?

---

### Post by descendent87 on 2009-08-15
I installed ubuntu from alpha 4 cd, then installed kubuntu-desktop and tried to remove as many gnome/gtk programs as possible and they were a few of the ones that couldnt be removed without taking kde with it

---

### Post by Bachstelze on 2009-08-15
> **descendent87 said:**
> I installed ubuntu from alpha 4 cd, then installed kubuntu-desktop

That's your problem. kubuntu-desktop is not just a KDE desktop, it has lots of extras, some of which require Gnome deps. If you want a pure KDE desktop, install [font=monospace]kde-core[/code].

---

### Post by descendent87 on 2009-08-15
the main problems seem to be update-notifier-kde (which i'm guessing is needed), kpackagekit and k3b (both of which require no gnome/gtk deps on arch)

---

### Post by Bachstelze on 2009-08-15
[http://packages.ubuntu.com/karmic/k3b](http://packages.ubuntu.com/karmic/k3b)
[http://packages.ubuntu.com/karmic/kpackagekit](http://packages.ubuntu.com/karmic/kpackagekit)

No Gnome deps as far as I can tell. And by the way, no, update-notifier is certinly not needed. You can very well just do your updates with apt-get.

---

### Post by descendent87 on 2009-08-15
Found the problem, noticed on that page that both k3b and kpackagekit need policykit-kde or policykit-gnome, gnome version was already installed so obviously were using those instead which is linked to all the packages I listed at the beginning. As for update manager, i'll get rid of that then as I do all my updates from terminal anyway.
Thought there had to be some reason why there was so many gnome/gtk packages I couldnt remove.
Thanks

---

### Post by Darkshade on 2009-08-15
Why didn't you just install Kubuntu? :popcorn:

---

### Post by descendent87 on 2009-08-15
Haven't tried Gnome for a while so wanted to see what 2.28 beta was like (but couldn't see anything different from 2.26)

---

### Post by Merk42 on 2009-08-15
> **descendent87 said:**
> Haven't tried Gnome for a while so wanted to see what 2.28 beta was like (but couldn't see anything different from 2.26)

If you really want to see change on the GNOME front, install the GNOME Shell.

Whether or not it's **good** change is debatable.

---

### Post by descendent87 on 2009-08-15
Seen it, not impressed. Will give it a try once the beta is out

---

