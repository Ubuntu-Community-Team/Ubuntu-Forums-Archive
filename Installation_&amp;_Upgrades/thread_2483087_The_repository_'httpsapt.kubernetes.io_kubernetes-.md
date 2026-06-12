---
title: "The repository 'https://apt.kubernetes.io kubernetes-xenial InRelease' is not signed."
date: 2023-01-20
forum: Installation &amp; Upgrades
---

### Post by joksik on 2023-01-20
hello today when i want install updates i have this error:


sudo apt-get update && sudo apt-get upgrade

Err:6 [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kubernetes-xenial InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B53DC80D13EDEF05
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kubernetes-xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B53DC80D13EDEF05
W: GPG error: [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kubernetes-xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B53DC80D13EDEF05
E: The repository 'https://apt.kubernetes.io kubernetes-xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.

after i search i try fix this with this command:

curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg

but it`s not help i have the same error

---

### Post by yancek on 2023-01-20
Ubuntu Xenial is 16.04 for which standard support ended almost 2 years ago (April, 2021).  You can get extended support, see the links below.  It is necessary to pay for this service.  

[https://ubuntu.com/16-04](https://ubuntu.com/16-04)

[https://computing.cs.cmu.edu/news/2020/eol-ubuntu-1604](https://computing.cs.cmu.edu/news/2020/eol-ubuntu-1604)

---

### Post by joksik on 2023-01-20
ok thx for quick answer so how can i delete this xenial from my update list ?

ok i figureout myself how
sudo rm /etc/apt/sources.list.d/kubernetes.list
sudo rm /etc/apt/sources.list.d/kubernetes.list.distUpgrade

now works fine ;)

---

### Post by ActionParsnip on 2023-01-20
I recommend you upgrade to a supported release. Xenial is dead and gone

---

