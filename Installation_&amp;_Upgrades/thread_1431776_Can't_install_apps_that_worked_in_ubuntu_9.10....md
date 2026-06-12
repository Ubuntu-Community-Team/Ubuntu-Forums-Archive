---
title: "Can't install apps that worked in ubuntu 9.10..."
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by Hawk__0 on 2010-03-17
Are Kubuntu and Ubuntu 9.10 really that different?

I can't install boxee with the deb provided from the site as I did in ubuntu 9.10.  I get unmet dependencies.  I also have no gui manager for deb packages as ubuntu had.

---

### Post by sikander3786 on 2010-03-17
Hi.

If you want to use Kubuntu applications on Ubuntu, you need all those KDE libraries and to use Ubuntu application on Kubuntu you'll surely need GNOME libraries.

However we can use all those stuff from KDE and GNOME on both Ubuntu and Kubuntu e.g, I am using Amarok on Ubuntu but that makes Amarok a lot slower than on Kubuntu. You guess why....?

Either way you should be able to run all the applications here and there. Just use the package manager of KDE and that should solve all the dependencies.

Sikander.

---

### Post by Chame_Wizard on 2010-03-17
In Konsole,to install debpackages:
```
sudo dpkg -i packagename.deb
```

To have the gui manager for deb packages:
```
sudo aptitude install gdebi gdebi-core gdebi-kde
```

Download and install the dependency *getlibs* for Boxee.
:popcorn:

---

### Post by Hawk__0 on 2010-03-17
Thanks Chame_Wizard! I couldn't find that dependency you were referring to but boxee installed when I used the gui deb installer.

---

