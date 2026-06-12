---
title: "Hoary Packages List"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by spartas on 2005-03-14
When I upgraded to hoary (about 4 or so months ago), I did not realize that I was still using most of the warty packages (albeit upgraded ones).  I searched this forum far and wide for a list of packages to upgrade to, but wasn't able to find one.  I am starting this thread as a package list, so it will hopefully be easier for other users to upgrade to hoary packages.

One such example:
While browsing this forum, I heard talk of the new xorg window subsystem and composite.  I naturally assumed it was installed on my machine, but xcompmgr wasn't working right because I still had (drumroll) **XFree86**!  How'd that happen?! I was running hoary.  After apt-get remove xserver-xfree86 (and apt's coresponding install xserver-xorg) I was set.

Here are some packages that I needed to manually apt-get install.

xserver-xorg
update-manager
update-notifier
xcompmgr

These four are all I can think of right off hand, but anyone is free to contribute to this list.

Supporting the latest and greatest ubuntu!

---

