---
title: "how do you downgrade libraries? (specifically qt libraries)"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by shein on 2008-08-18
Not sure if this is the right category to post this problem, sorry if it's not!

I had hardy-backports checked in hardy, and i must have installed the newest version of the qt libraries (4.4) without being aware of it.  This has caused some problems for me (primarily with skype video), so I'd like to downgrade to 4.3.4 (see [http://ubuntuforums.org/showthread.php?t=795676](http://ubuntuforums.org/showthread.php?t=795676) for why).  The only way i can think of doing this is uninstalling them, unchecking backports, reloading, then installing the old version.  the only problem is there are a lot of qtlib packages and I'm not sure which ones to uninstall. can anyone help?

also, is there any easier way to downgrade?

thanks!
Shawna

---

### Post by Partyboi2 on 2008-08-18
Can you force an earlier version in synaptic? Open synaptic and search for the qt package you want to downgrade then highlight it and select "Package" then "force version" then choose the version you want to use.

---

### Post by shein on 2008-08-18
thanks, it looks like i can choose that option for libqt4-core, but when i try to do it it gives me this error: 

E: /var/cache/apt/archives/libqt4-core_4.3.4-0ubuntu3_i386.deb: trying to overwrite `/usr/share/qt4/translations/qt_ar.qm', which is also in package libqtcore4

I figured this might mean i need to downgrade libqtcore4 as well, but when i look at that the "Force version" option is greyed out. :(

---

### Post by shein on 2008-08-18
oh also i tried the force version for libqt4-gui, and it says a bunch of packages need to be removed including kdebase-runtime as well as others... 

is this ok? (sorry if this is a dumb thing to ask, just dont want to mess up my entire windows manager)

---

