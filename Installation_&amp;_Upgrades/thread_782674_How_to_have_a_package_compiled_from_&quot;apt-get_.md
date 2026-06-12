---
title: "How to have a package compiled from &quot;apt-get source&quot; not updated?"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by dentament on 2008-05-05
The official ubuntu gftp-gtk package comes without ssl support (I posted a bug report on this matter at [https://bugs.launchpad.net/ubuntu/+source/gftp/+bug/226832](https://bugs.launchpad.net/ubuntu/+source/gftp/+bug/226832)).
I managed to build an alternative .deb with ssl enabled by using "apt-get source gftp-gtk", removing the "--disable-ssl" line from "gftp-2.0.18/debian/rules" file (and the trailing "/" from the previuos line), and running "dpkg-buildpackage -b -uc" in the "gftp-2.0.18" directory; then I installed it. It works, but as soon as I installed it the update manager began notifying it has to be updated to (substituted with) the official one, and it continues this way even after having it marked with "hold".
Why doesn't "hold" work?
Is it possible to prevent ubuntu from trying to update the "modified" package?
Thanks for any suggestions

---

