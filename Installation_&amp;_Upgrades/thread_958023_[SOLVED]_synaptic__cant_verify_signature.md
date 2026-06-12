---
title: "[SOLVED] synaptic : cant verify signature"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2008-10-24
i got this message when running a synaptic update/check ... 

[b]
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
[/b]

---

### Post by scragar on 2008-10-24
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
it does say so on the guide.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by james_bandido on 2008-10-25
@scragar, thanks very much ... 

please consider this thread solved/closed ...

---

