---
title: "How to prevent certain packages from being installed via upgrade"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-03-29
For example, I've uninstalled gnome-panels because I use AWN and the only way to get rid of the panels completely is to uninstall it. During some updates in the last few days, it got re-installed. I never noticed it in the list of updates, until I rebooted and a panel appeared on the desktop. So I've uninstalled it. Again.

There may be other ways to hide the panels, but what about evolution? I've uninstalled that because I prefer Thunderbird.

This is only a problem when upgrading from one release of Ubuntu to the next.

---

### Post by xebian on 2009-03-29
You can use APT pinning.  There are many how2s thru google.  You want to 'pin' a package.  For example, I compile my arora browser so I don't want any from the repos, so I add these in the /etc/apt/preferences file

> 
Package: arora
Pin: version 0.6
Pin-Priority: 1001


---

