---
title: "How to move panels around in Jaunty"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-02-22
I just updated my nvidia driver in Jaunty to 180 with dual screens and now I'm stuck with the panel that was originally on the second monitor now in the first monitor. It's not moving by drag and drop like it did in Intrepid.

I upgraded from Intrepid to Jaunty, so I'm not sure if anyone else is seeing this or if it is a bug picked up along with the upgrade.

Is this an error/bug and also, what file do I need to edit to move it to the second monitor?

---

### Post by Naddiseo on 2009-02-22
It's a design decision; you now have hold alt down while you drag it. I've submitted a patch upstream that adds monitor switching to the properties dialog of the panel.

---

### Post by kyleabaker on 2009-02-23
> **Naddiseo said:**
> It's a design decision; you now have hold alt down while you drag it.
Thanks for clearing that up for me! It was annoying me like crazy, haha.

> **Naddiseo said:**
> I've submitted a patch upstream that adds monitor switching to the properties dialog of the panel.
Happen to have a link to the submission so I can track it (in launchpad I assume)?

---

### Post by Naddiseo on 2009-02-23
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/321032](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/321032)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/192009](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/192009)
[http://bugzilla.gnome.org/show_bug.cgi?id=562944](http://bugzilla.gnome.org/show_bug.cgi?id=562944)

---

