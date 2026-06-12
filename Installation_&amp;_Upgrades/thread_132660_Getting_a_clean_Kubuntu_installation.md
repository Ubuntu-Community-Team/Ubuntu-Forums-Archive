---
title: "Getting a clean Kubuntu installation"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by nickle on 2006-02-18
Many people myself included have complained that Kubuntu does not seem to be as good an implementation of KDE as is found on other distributions such as SUSE for example.
Part of the reason for this is that many users, like myself who are not so technically astute had also installed the ubuntu-desktop. This is a big mistake if you want a nice ordely clean KDE desktop. The Ubuntu-desktop instally all the gnome stuff on top of your kde installation and makes everything very messy.

My recommendation is that once you have decided which interface you need remove all the stuff you don't need/want belong to the other.  The mixing that often happens inadvertently gives a bad impression of the KDE implementation.

I have said this several times and I will say it again, it is a big mistake that a clearer distinction is not made between Ubuntu the linux distrinution and Ubuntu the linux distribution with a gnome interface. It leads to unnecessary confusion and is strongly biased against the KDE implementation. While I don't think this is on purpose, it is a serious historical flaw in the nomenclature...

---

### Post by knalle on 2006-02-18
or install just the **base system** and then do **apt-get install kubuntu-desktop**

---

### Post by nickle on 2006-02-18
All well and good if you do this and know this is all you need to do. However if you read the text of the Ubuntu desktop description:
The Ubuntu desktop system:

[I]This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).[/I]

and do not know (out of ignorance, I admit) this this exclusively refers to the Gnome interface, you end up with a messy KDE desktop. For example it would be useful to mention in the above description for example that this refers exclusively to Gnome packages....

---

### Post by knalle on 2006-02-18
well gtk is pretty nice to have even if you run kde, so some dependecies will always be there, ofcourse nothing stops you from installing the **base system** and then install kde packages only

---

### Post by nickle on 2006-02-18
[QUOTE=knalle]well gtk is pretty nice to have even if you run kde, so some dependecies will always be there, ofcourse nothing stops you from installing the **base system** and then install kde packages only[/QUOTE]


Why do you need it? Surely apt will take care of any dependencies which might arise if you want one or the other gtk based package... or am I missing something here?

---

### Post by knalle on 2006-02-18
eh, thats what im saying "nothing stops you from installing the base system and then install kde packages only", i personally have gtk installed because i use gimp, but you dont have too

---

