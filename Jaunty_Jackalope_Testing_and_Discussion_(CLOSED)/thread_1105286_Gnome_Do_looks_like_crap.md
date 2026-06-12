---
title: "Gnome Do looks like crap?"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Quift on 2009-03-24
Hi again, 

Now off to solve the minor annoyances.

Gnome Do currently looks like crap! It used to be crisp, black and white using my icon set rendered at the correct size.

Now instead it displays blue instead of black, the icons look like pixeled paint, and the gnome-do icon doesn't display in the notification tray so I can't reach to alter it in any way.

Please, what am I missing?

Thanks for your help.

---

### Post by scaine on 2009-03-24
You might try posting a screenshot of the issue.  If you call up gnome-do, there's a little icon at the top-right of the gnome-do window which should let you start the preferences dialogue.  What theme are you using?  Do you definitely have compositing enabled, which I think gnome-do requires (or is it just Docky... I might be wrong on that one).

---

### Post by Quift on 2009-03-24
Thanks, that sort of helped. Now half of the icons look great, and the other half looks crap.

How do I enable compositing?

---

### Post by jfernyhough on 2009-03-24
Either enable Compiz (System, Preferences, Appearance, Visual Effects) or enable compositing in Metacity.

Two ways I can think of, one is to use Ubuntu Tweak ( [http://www.getdeb.net/](http://www.getdeb.net/) ) or run gconf-editor, go to Apps, metacity, general, and tick the box compositing_manager.

You'll also need a 3D-accelerated driver to get this working (Intel works OOTB, nVidia and ATi will likely need drivers).

---

### Post by Tich666 on 2009-03-24
System -> Preferences -> Appearance -> Visual Effects -> Normal or Extra.

You can also open a terminal and run compiz or use fusion-icon to change the compositing options.
To enable certain effects and plugins, install ccsm.

gnome-do looks fine here, using the docky skin with metacity compositing.
A few icons look blurry, most noticeable open office apps, but they're the exception rather than the rule for me.

---

### Post by Technoviking on 2009-03-24
There is a bug filled on the blurry icons.
[https://bugs.edge.launchpad.net/do/+bug/323153](https://bugs.edge.launchpad.net/do/+bug/323153)

T-V

---

### Post by go7Ul1ai on 2009-03-24
> **Technoviking said:**
> There is a bug filled on the blurry icons.
[https://bugs.edge.launchpad.net/do/+bug/323153](https://bugs.edge.launchpad.net/do/+bug/323153)

T-V

This is not a Do bug, it's the Human Icon Theme not being scalable. Canonical should really re-do the theme :/

Edit: [https://bugs.launchpad.net/human-icon-theme](https://bugs.launchpad.net/human-icon-theme)

Looks like no ones going to fix anything any time soon

---

