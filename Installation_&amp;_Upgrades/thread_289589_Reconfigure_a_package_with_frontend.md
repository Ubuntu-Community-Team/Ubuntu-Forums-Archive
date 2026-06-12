---
title: "Reconfigure a package with frontend"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Frunktz on 2006-10-31
Hi!
I have installed samba-common, after unpacking I have a basic frontend (Dialog) that let me configure some options.
Now if I want to reconfigure some option I can that in two ways:
- dpkg-reconfigure samba-common
- edit /etc/samba/*.conf

Little problem, dpkg-reconfigure do anything, more exactly he reconfigure the package but won't let me see the graphical fronted.
I try to remove and reinstall but same situation, so I remove again and PURGE the config file.
When I reinstalled the package the fronted appears.
I think I can see the frontend for reconfigure package without purge configuration file...I guess is debconf but I don't know what use that.

Suggestion?

Thanks

---

