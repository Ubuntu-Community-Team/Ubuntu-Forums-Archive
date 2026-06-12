---
title: "Get error &quot;run dpkg --configure -a&quot; when starting Update manager"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by antlachance on 2008-06-13
When ever I start Synaptic Update manager i get the following error message:

"An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Any help would be appreciated on the matter of fixing the issue.

---

### Post by ibutho on 2008-06-13
Run Applications -> Accessories -> Terminal and enter 
```
sudo dpkg --configure -a
```

---

### Post by antlachance on 2008-06-13
Thank you very much.  I am new to Linux and i have to say one of the biggest pluses is the community.  No other OS can even compare.

---

