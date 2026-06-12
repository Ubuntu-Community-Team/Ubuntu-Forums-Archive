---
title: "OpenOffice wants to install KDE?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by picpak on 2006-06-03
I just upgraded to Dapper this morning, and noticed it removed OpenOffice (among other things...but I've got those back up and running).

OpenOffice doesn't want to install through apt-get, so I went in Synaptic to install it and got this:

To be removed:

openoffice.org-debian-files

To be installed:

kdelibs-bin
kdelibs-data
kdelibs4c2a
libarts1c2a
libavahi-qt3-1
libopenexr2c2a
libqt3-mt
libxmlsec1
libxmlsec1-nss
libxmlsec1-openssl
menu-xdg
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-impress
openoffice.org-java-common
openoffice.org-kde
openoffice.org-l10n-en-us
openoffice.org-math
python-uno

Is this normal? Or can I install OpenOffice without having to install KDE files?

---

### Post by Ragazzo on 2006-06-03
I had to reinstall OpenOffice too after upgrading but it didn't install any of those KDE files for me. I had to manually select openoffice.org-gnome to get the graphics right.

---

### Post by picpak on 2006-06-04
That was easy enough, I just selected openoffice.org-gnome and it did it all for me.:D

---

### Post by RavenOfOdin on 2006-06-04
I had to reinstall OpenOffice too, but it removed its own -debian package.

There should now be some libraries available in Synaptic to integrate OO with KDE. You may want to check them out if you're a fan or just did the old "wham and bam" routine on Kate.

---

