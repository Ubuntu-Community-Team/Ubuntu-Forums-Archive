---
title: "Update Manager"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by majkmil on 2006-05-18
When I upgraded to Dapper I was told to use this command ( gksudo "update-manager -d" ) so update manager would look for beta upgrades. After a successful upgrade ( yoo hoo ) I get update notifications that I think I already got when upgrading. Do I need to switch update manager back to default and if so can someone show me how this is done? Should I just leave it alone? Thanks

---

### Post by Sef on 2006-05-19
use this to install any upgrades:

Terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by majkmil on 2006-05-19
Thanks Sef, I know how to dist upgrade but what I need to know is should I undo this command I used to force UPDATE MANAGER to search for pre releases. (gksudo "update-manager -d). It seems that I am getting update notification everyday, some I am sure I already have the latest version.

---

### Post by deweese on 2006-05-21
A

---

