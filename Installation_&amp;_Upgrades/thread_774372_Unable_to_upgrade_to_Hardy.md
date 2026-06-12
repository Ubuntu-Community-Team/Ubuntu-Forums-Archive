---
title: "Unable to upgrade to Hardy"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by PolR on 2008-04-29
I have gutsy. I can't upgrade to Hardy because the file download abort on an error message:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-doc_2.5.2-2ubuntu4_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-doc_2.5.2-2ubuntu4_all.deb) Hash Sum mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dbg_2.5.2-2ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dbg_2.5.2-2ubuntu4_i386.deb) Hash Sum mismatch

---

### Post by PolR on 2008-04-29
Found the problem. it is the server for Canada that is unusable with wrong MD5hashes. It also happens to be painfully slow. Switching to another server fixes everything. :popcorn:

---

