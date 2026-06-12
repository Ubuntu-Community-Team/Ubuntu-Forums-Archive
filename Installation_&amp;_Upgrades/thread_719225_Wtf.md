---
title: "Wtf?"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by jalyst on 2008-03-08
Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '27262979' '--update-at-startup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.


Any ideas?

---

### Post by taurus on 2008-03-08
Are you the the user that created during the installing process?  What happens when you run these two commands from a terminal?  Make sure you have shut down synaptic first though.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

