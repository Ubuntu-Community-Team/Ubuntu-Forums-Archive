---
title: "Broken Cups"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by NoJock on 2007-01-17
OK im new and lost in Dapper my printer works great hp Desk jet 820ces, however have installed Edgy 6.10 on a different partition  and printer will not work. Cups takes a long time to load and doesn't find the printer on the local port lpt1. Does any one have a suggestion as of where to look?](*,)

---

### Post by bapoumba on 2007-01-17
Hello,
**sudo adduser cupsys shadow**
and you will be able to manage your printer from cups admin interface. Open **localhost:631** in a web browser.

---

### Post by NoJock on 2008-07-21
Thanks, bapoumba have moved on to 7.04 Ubuntu CE and no problems with that distro.

---

