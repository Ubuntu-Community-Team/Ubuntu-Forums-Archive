---
title: "kubuntu 6.10 upgrade?"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by stephan0h on 2007-04-02
Hi group,

I'm using kubuntu, ubuntu release 6.10. How would I go about when upgrading to the latest beta-release of ubuntu?

Thanks,
Stephan

---

### Post by Majorix on 2007-04-02
Well there are 2 options. Either a dist-upgrade or a clean install.

With dist-upgrade you can expect a drop in the performance. So what I suggest is doing a clean reformat then install.

If you insist on dist-upgrade, here is how to do it:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Hope it helps. Good luck!

---

### Post by stephan0h on 2007-04-02
> **Majorix said:**
> Well there are 2 options. Either a dist-upgrade or a clean install.

With dist-upgrade you can expect a drop in the performance. So what I suggest is doing a clean reformat then install.



You mean I need to reinstall from scratch? Ouch!

Other than that: why would a dist-upgrade degrade performance?

Thanks,
Stephan

---

