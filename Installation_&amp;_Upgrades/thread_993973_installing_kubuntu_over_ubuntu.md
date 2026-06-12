---
title: "installing kubuntu over ubuntu"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by jackwarr on 2008-11-26
I want to change from Ubuntu to Kubuntu.  How much, if anything, will I lose as far as settings and such?  Is there anything to look for here?

---

### Post by icanfly0307 on 2008-11-26
Hi,
      Changing from Ubuntu to Kubuntu will make you lose settings as they are not both the same. GNOME and KDE have different settings and are not intercompatible. To remove Ubuntu, type:

[FONT="Courier New"]sudo apt-get remove ubuntu-desktop[/FONT]

And finally, to install Kubuntu, type:

[FONT="Courier New"]sudo apt-get install kubuntu-desktop
[/FONT]
Let me know what happens. Good Luck! :)

---

### Post by snova on 2008-11-26
I suggest you just install the 'kde' package. Don't remove anything yet.

There's also 'kubuntu-desktop', which depends on a few other things, one of which is 'kde'.

---

### Post by icanfly0307 on 2008-11-26
If you're looking for KDE 4, try sudo apt-get install kde4. However, this will not install the full functionality of a Kubuntu desktop.

---

