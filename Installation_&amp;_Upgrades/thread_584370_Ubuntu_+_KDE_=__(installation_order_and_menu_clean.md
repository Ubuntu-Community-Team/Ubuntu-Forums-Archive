---
title: "Ubuntu + KDE = ? (installation order and menu cleanup...)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Finch75 on 2007-10-20
Hello everybody,

disclaimer: I'm still a Linux newbie, so I hope I get all the terms right :-) I did search the forums first and found a few helpful posts but none that answers all my questions...

I want to use KDE instead of Gnome BUT it seems like I prefer most of the applications from Ubuntu to the ones in Kubuntu. For example, I like Synaptic a lot better than the thing in KDE (aptitude?), I want OpenOffice instead of KOffice, I want Firefox instead of Konqueror... and so on.

How do I do this? I did my "first steps" in Linux in Feisty. First I installed Ubuntu, then I installed "kde-desktop". That's what everybody in the forum says. I did work, BUT:
- quite a few things in KDE didn't work (configuring menus and some other things). Also, iirc, some programs didn't prompt for the su-password although they should have (instead, they didn't work). I don't know if this would've happened in a "plain Kubuntu installation". I sure hope not...
- the menus were totally cluttered with all the Ubuntu and the Kubuntu software mixed and mingled. That was very confusing.

So what should I do?

A related question: Will it make a difference if I install "Ubuntu + kde-desktop" or "Kubuntu + gnome-desktop"? Should I maybe install "Ubuntu + kde-code (?) + ...?" What do I need to install so I can use the KDE desktop?

AND if I install both, can I still tell which is part of Ubuntu and which is part of Kubuntu? Are there any steps I can / should take before I install both?

Thanks for any hints!

---

### Post by LaRoza on 2007-10-20
```
sudo aptitude install kde-core
```

You will have all you Ubuntu apps, and a few K apps. I experienced no problems with this. The apps will be in the Ubuntu menu's, but there are not a lot.

This will install the least amount.

---

### Post by perlluver on 2007-10-20
Fist sudo apt-get install kubuntu-desktop.  Ubuntu and Kubuntu items will be mixed together, you can tell the difference by most Kubuntu items will show an icon, ubuntu's will be blank.  You can still use Gnome products in Kubuntu, I am using synaptic, and alot of other gnome things.  Hope this helps.

---

