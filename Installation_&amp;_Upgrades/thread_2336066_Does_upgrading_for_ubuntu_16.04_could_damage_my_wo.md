---
title: "Does upgrading for ubuntu 16.04 could damage my work?"
date: 2016-09-04
forum: Installation &amp; Upgrades
---

### Post by roishik on 2016-09-04
Hello,
I'm currently working on Linux ubuntu 14.04, and most of my work is about python development (deep learning using 'caffe').
**Is upgrading to ubuntu 16.04 could create incompatibility** with existing packages like 'caffe' or 'Anaconda' program (for python 2)? 

Thanks a lot!
Roi

---

### Post by TheFu on 2016-09-04
Welcome to the forums.

Any major upgrade can cause issues to custom environments or complex applications.  This is why having full, complete, recoverable, backups is mandatory before attempting any major system change.

If you follow the best practice for all developers, then you'll have your own python environment and won't trust the OS installed python at all.  Re-installing that should be expected, since libc will change.  Whether any programs written by you need to be modified is a completely different question. Guess it depends on how close to the OS those programs are written. Most of the time, if the same level of language is being used and all the libraries for that language have been recompiled for the new OS/libc, then everything will be fine.

Or everything could go just fine.  No way to know. Sorry.

---

