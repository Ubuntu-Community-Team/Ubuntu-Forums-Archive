---
title: "GPG error during updating"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by rwynns on 2008-08-25
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Can anyone help with this problem?

Thanks in advance,

---

### Post by Partyboi2 on 2008-08-25
Re-add the key. Open a terminal (Applications>Accessories>Terminal) and
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by rwynns on 2008-08-26
Thanks, That fixed it....

---

