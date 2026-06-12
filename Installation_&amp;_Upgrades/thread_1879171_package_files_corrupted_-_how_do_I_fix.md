---
title: "package files corrupted - how do I fix?"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2011-11-11
Due to an unexpected shutdown, something has gone wrong with the package cache and running "apt-get check" gives this error:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

Attempts to start the upgrade manager or synaptic result in similar messages.

Any suggestions for fixing this?

---

### Post by BillyBoa on 2011-11-11
There is a package integrity check here [https://launchpad.net/ubuntu/oneiric/+package/system-integrity-check](https://launchpad.net/ubuntu/oneiric/+package/system-integrity-check)
But I'm not sure if it helps
11.10 has already installed an integrity check but I don't remember where you can find it.

---

### Post by wyliecoyoteuk on 2011-11-11
You need to rebuild the package list:

[http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)

---

### Post by Colin@oxford on 2011-11-11
Thanks - that did it. (I knew it had to be easy :) )

---

