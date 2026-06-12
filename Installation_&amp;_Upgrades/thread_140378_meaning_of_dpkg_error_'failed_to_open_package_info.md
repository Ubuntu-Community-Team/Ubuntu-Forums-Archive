---
title: "meaning of dpkg error 'failed to open package info file '"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by jal on 2006-03-06
Got the .deb from opera but dpkg reports the error below.
I had opera going on 5.04 but upgrade to breezy killed it.
Not sure if '.../control' file is something I need to create, or if I've missed a step along the way (i.e. I'm new to this).

```

$ sudo dpkg -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
dpkg: error processing opera_8.52-20060201.6-shared-qt_en_etch_i386.deb (--install):
 failed to open package info file `/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory
Errors were encountered while processing:
 opera_8.52-20060201.6-shared-qt_en_etch_i386.deb

```

---

### Post by WackToMack on 2006-03-06
I'm not 100% sure, but it could be a dependency problem. :D

---

### Post by jal on 2006-03-07
automatiKs - that did it. Opera lives.
Not sure how though.


Thanks, WackToMack

---

