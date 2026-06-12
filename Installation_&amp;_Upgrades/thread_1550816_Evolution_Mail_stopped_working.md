---
title: "Evolution Mail stopped working"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by Sodear on 2010-08-11
Evolution e-mail has stopped working.  Un-installed everything evolution using Synaptic and re-installed. No change: address book comes up but mail, calendar etc do not work.  Clicking on any causes gray out and leads to a force quit.
So how do I un-install evolution completely and then re-install as a completely fresh install.  I am using Ubuntu 10.04 Lucid Lynx.

---

### Post by lechien73 on 2010-08-11
Did you mark the package for "Complete Removal" in Synaptic? You could also do:

```
sudo apt-get purge evolution
```

---

### Post by Sodear on 2010-08-11
Thanks for your posting.  So I purged Evolution via Terminal and for good measure re-started the computer.  Now I can't get in at all, it won't recognize my password: so I guess I have to hunt for help on that.  Thanks, anyway.

---

