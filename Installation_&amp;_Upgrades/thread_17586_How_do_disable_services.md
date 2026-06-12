---
title: "How do disable services"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by freemanen on 2005-03-01
for example if sendmail is runing how do i get it not to run?

---

### Post by Juergen on 2005-03-01
For each runlevel x you have a link in /etc/rcx.d to a script in /etc/init.d for the services that are to start/stop when entering this runlevel.
(Links beginning with S start, those beginning with K stop a service)

You could just remove these links.

If you don't want to do it manually look at (man) 'update-rc.d', and/or install rcconf which is a frontend for update-rc.d

---

### Post by alastair on 2005-03-01
Use :

update-rc.d

see : man update-rc.d

e.g.

update-rc.d -f sendmail remove

This removes the links.

---

