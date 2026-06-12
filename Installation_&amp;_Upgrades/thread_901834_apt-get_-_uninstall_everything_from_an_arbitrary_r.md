---
title: "apt-get - uninstall everything from an arbitrary repository"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by ansichart on 2008-08-26
I added a third-party source to apt-get, and now I want to remove everything that was installed from that source.  How can I do this?

---

### Post by Pro-reason on 2008-09-26
> **ansichart said:**
> I added a third-party source to apt-get, and now I want to remove everything that was installed from that source.  How can I do this?

You should be able to open Synaptic, click on “Origin”, find the repo, and see a list of all packages from that repo.  It is then easy to make sure than none are installed.

There's probably some fancy command-line way too.

---

### Post by zxscooby on 2008-09-26
dpkg -l | grep whateversearchtermyouwanttofind
will list packages installed.

---

