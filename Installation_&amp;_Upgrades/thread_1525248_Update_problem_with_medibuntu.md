---
title: "Update problem with medibuntu"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by primal23 on 2010-07-06
I was doing an update today and got the following error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

I have tried updating the keys, and got this:

apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" 6 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 6

Any ideas?  Thanks

---

### Post by primal23 on 2010-07-07
bump

---

### Post by afrodeity on 2010-07-12
Same here. Looks okay though. There's a medibuntu mirror you could try.

---

