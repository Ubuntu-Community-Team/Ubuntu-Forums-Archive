---
title: "Server: NO restricted drivers"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Kleenux on 2007-12-02
Installing Gutsy Server first, then apt-get the Desktop ends up with no restricted drivers.

System > Admin > Restricted drivers manager popups

[FONT="Courier New"]You need to install the package
  linux-restricted-modules-2.6.22-14-server
for this program to work.[/FONT]

while the module doesn't exist... The "-generic" one does. This seems to be the reason why the wireless is not working.

*Questions*

1. Is it only a matter of naming, i.e. if I get the modules above as generic and rename (somewhere?) as 'server' will it get through?

2. Is there a way to bypass the R.D. interface, my wireless card is "Intel 3945ABG"?

3. Or can we expect a fix before the next release in April 2008 ?  (many people seem to be annoyed with this bug)


Thanks

---

