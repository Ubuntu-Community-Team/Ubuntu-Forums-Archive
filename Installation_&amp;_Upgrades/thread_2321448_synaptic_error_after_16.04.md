---
title: "synaptic error after 16.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2016-04-22
I installed xubuntu 16.04 64 bit yesterday and now get this error when I try to open synaptic, I've had no luck finding a fix
I also tried it without caps and without spaces
```
E: The value 'xenial xerus' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.
```

---

### Post by cvgaviao on 2016-07-26
I'm also having this same problem after upgrade ubuntu from 15.10 to 16.04 !

I found this question and its second answer helped me to fix the problem: [https://askubuntu.com/questions/770652/synaptic-aptitude-broken-after-upgrade-from-15-10-to-16-04/771844](https://askubuntu.com/questions/770652/synaptic-aptitude-broken-after-upgrade-from-15-10-to-16-04/771844)

---

### Post by QDR06VV9 on 2016-07-26
> **cvgaviao said:**
> I'm also having this same problem after upgrade ubuntu from 15.10 to 16.04 !

With Dist Upgrades it is a good idea if you run this.
```
sudo apt clean
```

---

