---
title: "Uncompressed documentation"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by yeti-dn on 2006-09-08
Documentation files above some size in /usr/share/doc are installed compressed presumably to save disk space.  But disk space is much cheaper than the human effort needed to deal with possibly compressed files.  cat, more, grep, ..., cannot be used directly and any attempt to find or extract some information by a script has to deal with nondeterministic file names (.gz or not) and decompression.  So I would like to install the documentation uncompressed.  Is it possible?

---

