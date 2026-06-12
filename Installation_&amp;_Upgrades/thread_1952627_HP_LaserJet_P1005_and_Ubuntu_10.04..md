---
title: "HP LaserJet P1005 and Ubuntu 10.04."
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by DrPhuzzichtkeit on 2012-04-04
It used to work, but now I am having a problem when trying to install HP LaserJet P1005 on Ubuntu 10.04? The automatic HP installer that pops up when I start the computer outputs the following message:
```
Receiving digital keys: /usr/bin/gpg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0xA59047B9
error: ERROR: Plug-in file does not match its digital signature. File may have been corrupted or altered. Error code: 2
```

Problem is that the **hplip** version in the repository is too old, and must be upgraded.

Here is what to do:

Open a terminal and type:
```
sudo apt-add-repository ppa:hplip-isv/ppa
sudo apt-get update
sudo apt-get install hplip
```

Then just start your printer, and it should work.

---

