---
title: "Wine budgetdedicated gpg key"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by nev0 on 2007-01-14
I'm sorry if this has been asked before but I couldn't find it in the forums and it's not listed on their site. I'm trying to install edgy Wine package but I'm getting the following errors on update

```
W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
```

I know I can still install Wine but I'd like my console to be error free :P, I just did a clean up of gpg keys so perhaps I accidentally deleted the key. Can someone give me the command to import the key from somewhere?

---

### Post by storm_mohamed on 2007-01-15
I was having the same problem, and i found the following answer at that forum.

THE SOLUTION:
// start
To make it go away forever, you need to add my key into your list of keys that APT will use. Just put the following into a terminal:

Code:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
// end

---

