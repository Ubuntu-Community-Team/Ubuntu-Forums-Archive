---
title: "Apache2 update breaks PHP?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by pinn8 on 2010-03-12
I'm running 8.04 Server LTS and havig a problem with the most recent apache2 package updates.  The updates (version [COLOR=Black]2.2.8-1ubuntu0.15) break php5.  All of my PHP pages show up in Firefox with a prompt for me to download an object of type application/x-httpd-php.

Looking at the install logs for the package updates, it appears that php5-mysql and libapache2-mod-php5 are uninstalled by the apache2 update, and never reinstalled. Simply re-installing these modules with apt-get does not fix the problem.  

Can anybody offer any suggestions for how to get my LAMP stack working again?[/COLOR]

---

### Post by pinn8 on 2010-03-14
bump.  Any ideas?

---

