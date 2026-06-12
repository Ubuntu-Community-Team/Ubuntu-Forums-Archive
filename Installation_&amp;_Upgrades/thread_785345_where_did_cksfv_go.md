---
title: "where did cksfv go?"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by gusto on 2008-05-07
I upgraded to the Hardy Heron the other day, and now I noticed cksfv is missing and its no longer in the repository. 

Will it be brought back, or what am I supposed to use instead?

---

### Post by ceagan on 2008-05-10
I don't know why it was pulled, but I think you can use cfv.

---

### Post by starscalling on 2009-06-18
cfv tosses errors:
/var/lib/python-support/python2.6/cfv.py:670: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/var/lib/python-support/python2.6/cfv.py:699: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
I don't recognize the type of Desktop/[blah filename goes here]

[edit]

karmic worked fine:
[http://packages.ubunut.com/karmic/cksfv](http://packages.ubunut.com/karmic/cksfv)

enjoi

---

