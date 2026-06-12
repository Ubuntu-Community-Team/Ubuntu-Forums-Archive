---
title: "Inaccessible root"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by ramtap on 2005-05-11
I've had a smooth installation & am so far very happy with this distro - with the one exception I can't seem to su to root! During the install I wasn't given the opportunity to set a password for root, and if I try to su - it fails for the password. 

Is there a default password? Or will I have to reinstall?

---

### Post by mrtaber on 2005-05-11
Not at all; the intention is that you use 'sudo' to do things that require root; however, if you really want to enable root and give it a password, just use the following:

```
sudo passwd root
```

After entering this in the terminal, you'll be prompted first for your password; next, you'll be prompted for the root password (and then asked to verify by entering it again).  Easy as that.  No reinstall required.

Mark :)

---

### Post by ramtap on 2005-05-11
Thanks for the quick reply! Thats worked fine.

---

