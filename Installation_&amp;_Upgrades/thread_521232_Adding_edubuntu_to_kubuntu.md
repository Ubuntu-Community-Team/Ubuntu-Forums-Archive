---
title: "Adding edubuntu to kubuntu"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by rzj on 2007-08-09
I've been looking for info on adding the edubuntu tools to an existing kubuntu or ubuntu feisty setup.

I came across instructions to add it...

sudo apt-get build-dep edubuntu-desktop

sudo apt-get install edubuntu-desktop

... however from reading that thread it seems this made edubuntu desktop setup the default for all new accounts.

Does it then allow you to select the desktop at login in the way you can switch between gnome and kde? Or do you just end up with a limited set of apps available as defined by the edu config?

What I really want to do is to add the edu apps to an existing kubuntu or ubuntu set up. Is there a list of the packages to apt-get to install them all including adding them to the desktop menus?

How do I make sure it is UK-English spellings - I assume this is available as a language option in edubuntu?

BTW is there a dedicated edubuntu forum? I couldn't find one, and the edubuntu wiki links seem to point to empty work-in-progress stuff.

Thanks,
Ray

---

### Post by splintercellguy on 2007-08-09
Yes, you can pick what window manager you wish to use at startup. If you install edubuntu-desktop you get all the wonderful apps.

---

### Post by forestpixie on 2007-08-09
> I came across instructions to add it...

you might be better of using aptitude

sudo aptitude install ... - I know it makes getting rid of Kubuntu/Xubuntu/Ubuntu easier, so I assume the same will apply


> Does it then allow you to select the desktop at login

Again I would assume so 

> What I really want to do is to add the edu apps

If you know the name of the apps you actually want you can just install them as normal with sudo apt-get or synaptic - I have done that for my youngest with the maths and typing apps.

Have a look at this page it might answer the apps question.

[https://wiki.edubuntu.org/EdubuntuInstalledApplications](https://wiki.edubuntu.org/EdubuntuInstalledApplications)

Edit - too slow by half :)

---

