---
title: "need to resize existing ubuntu partitions"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by derrick1985 on 2005-05-26
Hey

I have two linux partitions, both ext3. one root, and a home. I guess I should have researched first, but I made the root partition too big, and the home one too small. Is there anyway without having to reinstall, to give my home partition some more space from the root partition?

---

### Post by SFN on 2005-05-26
You can use gparted. Instructions for installing it are [here](http://ubuntuguide.org/#gparted).

---

### Post by rtz654 on 2005-05-27
or one less risky way: have you thought of creating a folder under / and making a symlink out of your /home

```
mkdir /shares
ln -s /shares ~/shares
chown user.groop /shares
```

---

### Post by skyboy on 2005-05-29
Hi,

Had the same problem of over sizing the root partition.
I did the following as proposed by rtz654
```

mkdir /shares
ln -s /shares ~/shares
chown user.groop /shares
``` 

Worked great :)
thanks

---

