---
title: "Upgrade to 16.04 deletes application I use"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by teknopaul on 2016-08-16
I recently upgraded to xenial xerus 16.04, ircd-ratbox has been deleted, no warning upgrade was going to delete applications.

aptitude search ircd-ratbox  shows

c   ircd-ratbox                                                                                 - advanced, stable and fast ircd

c meaning config files are still there but the application was deleted.

Its not available to install. I tried isntalled in a deb but it has dependencies issues.

Checking the launchpad web it seems that the xenial releease of ircd-ratbox is dependent on libs that have been deleted .

libgnutls-deb0-28

Any help with getting my IRCd server running would be appreciated, any idea why this happened so I can avoid it next time would be appreciated too.

---

