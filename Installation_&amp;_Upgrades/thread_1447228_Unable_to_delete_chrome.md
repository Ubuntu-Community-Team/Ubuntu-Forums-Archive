---
title: "Unable to delete chrome"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by pulsar91 on 2010-04-05
i am unable to delete chrome, i opened the sypnaptic manager but it says

'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->openn() failed, please report'

second i tried to find it in Add/Remove programs under the applications bar, couldnt find chrome in it.....

---

### Post by lisati on 2010-04-05
> **pulsar91 said:**
> i am unable to delete chrome, i opened the sypnaptic manager but it says

'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->openn() failed, please report'

second i tried to find it in Add/Remove programs under the applications bar, couldnt find chrome in it.....

Close synaptic and any other package managers you might have running, go to Accessories->terminal, and run:
```
sudo dpkg --configure -a
```

---

### Post by pulsar91 on 2010-04-05
this is what terminal says, once i entered the code

dpkg: parse error, in file '/var/lib/dpkg/updates/0231' near line 0:
 field name `1dd302d84465ac73dc3611cf25c73f02' must be followed by colon

---

