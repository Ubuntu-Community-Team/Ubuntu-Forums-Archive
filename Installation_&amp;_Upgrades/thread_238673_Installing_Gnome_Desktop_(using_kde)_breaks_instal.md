---
title: "Installing Gnome Desktop (using kde) breaks install"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by User_Program on 2006-08-18
Hi Everyone! 

I'm running into a problem trying to install gnome.  I'm using Kubuntu 6.06 

Here's the relevant parts of aptitude

First part
> The following packages are BROKEN:
  firefox-gnome-support libpoppler1-glib


Second part
> The following packages have unmet dependencies:
  libpoppler1-glib: Depends: libpoppler1 (= 0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 i                                                                                                   s installed.
  firefox-gnome-support: Depends: firefox (= 1.5.dfsg+1.5.0.3-0ubuntu3) but 1.5.                                                                                                   dfsg+1.5.0.5-0ubuntu6.06.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
evince [Not Installed]
gnome-desktop-environment [Not Installed]
libpoppler1-glib [Not Installed]

Downgrade the following packages:
firefox [1.5.dfsg+1.5.0.5-0ubuntu6.06.1 (now) -> 1.5.dfsg+1.5.0.3-0ubuntu3
(dapper)]


As for the firefox problem can I keep 1.5.0.5 and still use gnome?
As for the other problems I have no idea.  Any suggestions would be great!

Thanks

---

