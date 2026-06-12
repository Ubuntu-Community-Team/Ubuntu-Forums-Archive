---
title: "gconftool-2 undefined symbol error"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by acloserview on 2010-03-11
yesterday my gnome gui locked up during startup.
there is a problem with the "gnome power manager" package.

I get a pop-up saying "The configuration defaults for GNOME Power Manager have not been  installed correctly. Please contact your computer administrator."

tried:

"sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

sudo dpkg --configure -a

apt-get --reinstall install gnome-power-manager"


when trying to reinstall the gnome-power-manager package, I get the following error

gconftool-2 symbol lookup error: gconftool-2 undefined symbol gconf_schema_set_gettext_domain

any idea's? (only the terminal works)

---

### Post by cacaegg on 2010-03-14
I also face the same problem, does any one know the solution? thanks!

---

