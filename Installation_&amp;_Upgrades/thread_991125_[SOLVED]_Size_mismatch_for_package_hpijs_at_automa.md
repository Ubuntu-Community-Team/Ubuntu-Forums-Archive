---
title: "[SOLVED] Size mismatch for package hpijs at automated security update"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by helmut_ibm on 2008-11-23
Hi.

I use Ubuntu 7.10 and perform regular security updates. For a few days the update manager tries to update the package hpijs and some other related ones. If I try to install the updates, it downloads the package and then I get the message:

W: Failed to fetch [http://at.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://at.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch

Since I don't use this printer driver, I deinstalled all packages but hpijs. It still keeks asking me for updating this one package.

I cannot deinstall hpijs because it would also trigger the deinstallation of other packages I want do keep.

Can anybody tell me what I can do in order to fix that problem?

Greetings from Gurk
Helmut

---

### Post by Partyboi2 on 2008-11-24
Its a known problem, they are in the process of fixing it. So hopefully soon. :)

---

### Post by helmut_ibm on 2008-11-27
Thanks. One of the last updates has eventually worked.

---

