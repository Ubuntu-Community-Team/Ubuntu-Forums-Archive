---
title: "fix openssl 1.0.1 bug 12.04 sslv3 handshake failure"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by herebox on 2012-05-01
From 12.04 LTS

Want to upgrade these:
openssl (1.0.1-4ubuntu5) but libssl1.0.0 (1.0.1-4ubuntu5) 

Fixes [https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/986147](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/986147)

Is it possible to do using apt-get or do I have to do it from source?  

If I do have to do it from source, whats a way to update apt-get so that it knows what version is installed?  Related, when I tried apt-get install openssl 1.0.0 (rollback), it said it would be 2GB of new data?!

Thank you !

---

### Post by herebox on 2012-05-01
The bugfixes are in the proposed archive as described here: 
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Upgrading them worked great!

As far as the second question, I was using "apt-get install openssl 1.0.0" which wanted to install every package matching "1.0.0" -- 2GB worth.

The third, I still don't know the answer to, nor will I for today.

---

