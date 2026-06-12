---
title: "Installing software with a newer version than what is in the repository"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by jfenwick on 2008-09-18
Hi,

Rhythmbox has gone through many revisions since Hardy Heron was released. 

Is there an alternate repository where I can apt-get the newest version?

Or should I just install the software directly from the Gnome site? If I do that, should I uninstall Rhythmbox first? What will I need to install besides the default Rhythmbox?

---

### Post by pytheas22 on 2008-09-18
Ubuntu's policy is to provide software updates only for bug and security fixes, not for updated versions of a particular application (this keeps things more stable and predictable, if a bit outdated in some cases)--so the version of Rhythmbox that was available when Hardy was released last spring is the version that will always be available in the Hardy repositories. 

If you want a later version, one option is to compile the latest version of Rhythmbox from the source code available on Gnome's site.

A better and simpler option is probably to install the package of Rhythmbox available for Ubuntu 8.10.  You can download that package [here]("http://packages.ubuntu.com/search?keywords=rhythmbox&searchon=names&suite=intrepid&section=all").  I'm not sure if it will install with just that one package, however--there may be other packages upon which it depends that need to be more recent than the versions available in Hardy.  If you get an error trying to install that package, let me know and we can work around it--you can always temporarily enable the Ubuntu 8.10 repositories if necessary.

---

