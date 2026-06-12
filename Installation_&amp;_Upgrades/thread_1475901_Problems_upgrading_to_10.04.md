---
title: "Problems upgrading to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Faith95 on 2010-05-07
I go to "update manager" and there's a link there to upgrade to the latest version of Ubuntu. However whenever I do this, it says something about not being able to verify packages and cancels the download.. What could be the problem and how do I fix it?

---

### Post by kansasnoob on 2010-05-07
Just as a matter of troubleshooting go to terminal and run:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

I'm curious if that returns any errors.

---

