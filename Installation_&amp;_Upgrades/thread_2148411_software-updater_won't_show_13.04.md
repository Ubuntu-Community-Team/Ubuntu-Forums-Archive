---
title: "software-updater won't show 13.04"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by xadder on 2013-05-25
I am running xubunto 12.10, and would like to do a dist-upgrade (to 13.04, not 13.10, sorry!). A month ago I was offered the chance to upgrade by the software-manager, but wanted to wait. Now I can't get the system to show me an "upgrade" button at all. I have the option "notify me of new ubuntu" set in the Updates section. 

I prefer an upgrade to a clean install, so help appreciated to find a way to do it...Thanks.

---

### Post by Laiquendi on 2013-05-25
This is a command line version of upgrading release:

```
sudo aptitude install update-manager-core
sudo do-release-upgrade
```

---

### Post by xadder on 2013-05-25
Thanks. That seems to work! (Started anyway.....)

If all fails I'll do a clean install, but I enjoy the upgrade method :-)

---

### Post by xadder on 2013-05-25
Now running 13.04 :-)

Thanks!

---

