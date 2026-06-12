---
title: "Injecting a file, or package, before preseed installs the operating system"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by tdb2 on 2014-09-09
Hi,

I'm using preseed to install Ubuntu server on machines. One problem I have is with UID clashes between system accounts created by Ubuntu, and other external accounts I need to add. A fix for this seems to be to modify /etc/adduser.conf before packages are installed to change the range used for system accounts.

This seems simple in principal, but I'm not sure how to modify /etc/adduser.conf at the right point in the preseed install. If I could add the file to the new filesystem before packages are installed, that'd be fine. Or maybe I could create a custom package with just that file that could be installed before the adduser package (I've checked the source for adduser - it'll be happy if the file already exists when it gets installed).

Any pointers?

Tim.

---

