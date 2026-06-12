---
title: "Sticky sais to close all apps."
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Nordoelum on 2006-06-01
Greetings,
 
After reading the sticky I wonder how to close all the apps for an safe upgrade?
 
And do I need to change the repos before I do the update?

---

### Post by 3rdalbum on 2006-06-01
You don't need to change the repos before doing the update. If you have the latest version of the Update Manager, it will detect the new version available.

To close all programs, go into the System Monitor and then "View > All Processes". Get rid of those that you know are unnecessary for running the computer (i.e. ssh-agent, apache2, clock-applet etc). Don't just "select all" and click End Process, as many processes are necessary for use of the computer.

---

### Post by Khannie on 2006-06-01
I wondered the same thing. Is it safer / faster to do a /etc/init.d/gdm stop and run the upgrade from a shell login?

I've never done an upgrade before, and I have no alternative OS to fall back on. :)

---

