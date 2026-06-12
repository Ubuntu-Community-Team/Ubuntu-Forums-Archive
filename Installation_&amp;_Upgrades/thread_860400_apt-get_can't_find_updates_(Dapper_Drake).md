---
title: "apt-get can't find updates (Dapper Drake)"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by js31 on 2008-07-15
Hello,

I'm online with my new DSL connection for the first time using pppoe. everything works great only apt-get doesn't find any updates at all, the search for packages only checks locally, it seems. Notifier in taskbar shortly viewable than disappears when starting up KDE.

I tried some other commands I found during google and forum search, like 'sudo gksu &#8220;update-manager -c -d&#8221;', but not successful. Is there any alternative way to get updates or to fix the apt-get installation?

thanks in advance :)
Joerg

PS: please excuse if beginners question, I'm relatively new to linux

---

### Post by Pumalite on 2008-07-15
Are you talking about updates or do you want to upgrade to a newer version?

---

### Post by Pumalite on 2008-07-16
If you want to upgrade; you can try this:

sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

