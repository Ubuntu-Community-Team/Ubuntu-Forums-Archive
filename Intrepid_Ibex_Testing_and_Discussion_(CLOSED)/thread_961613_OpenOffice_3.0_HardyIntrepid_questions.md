---
title: "OpenOffice 3.0 Hardy/Intrepid questions"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by laptoplinux on 2008-10-28
On the web, I've found several sites that give instructions on how to install OO 3.0 in Hardy from the web site's deb package, but they all involve uninstalling OO from synaptic, and that takes quite a few packages along with it, such as ubuntu-desktop, aspell, etc.

Is it safe to remove all of those packages?  Will there be any system brokenness or instability afterwards?

Is there any other way to get OO 3.0 in Hardy? (I found one link to a PPA, but when I added it to the apt sources list, it didn't seem to work even after updating the package lists.)

As for Intrepid, I've already seen another PPA that supposedly has intrepid OO 3.0 packages ready to go.  Will installing Intrepid and then updating to these packages throw a wrench into future updates (for example the 00 3.0.1 bugfix release coming to Intrepid backports in December)?

Also, if I remember correctly, the Ubuntu version of OO also includes the Go-OO patches, so it is basically Go-OO instead of base OO, right?  If I install OO 3.0 from the official site, how would I go about getting the Go-OO changes merged in?  Maybe I should just wait for Go-00 3.0?

What it boils down to is that I would really like to get OO 3.0 sooner rather than later (with any enhancements or additional patches that come with the Ubuntu/Go-00 version), but I'm confused as to the best, non-system-or-update-breaking way to go about this due to the way OO is tied into other packages in Ubuntu.

---

### Post by NewJack on 2008-10-28
I followed these instructions and everything went flawlessly:

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

The only thing you have to worry about is uninstalling the > ubuntu-desktop metapackage.  You only have to worry about this if you are looking to upgrade to a new major version (ie: from Hardy to Intrepid).

---

### Post by sayems on 2008-10-28
$ sudo gedit /etc/apt/sources.list

Copy to the end of your sources.list

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by gjoellee on 2008-10-28
> **sayems said:**
> $ sudo gedit /etc/apt/sources.list

Copy to the end of your sources.list

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

yes that's the easy way, however if you want to keep away from command line use this tutorial you find here: [http://kshoster.net/node/56](http://kshoster.net/node/56)

---

