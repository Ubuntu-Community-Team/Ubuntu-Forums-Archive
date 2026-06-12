---
title: "where does the program go? install via apt-get"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by tanyeun on 2010-01-02
I used apt-get to install programs a lot
but I always have a hard time to know where the program installed to
most of the exec of the program is the same name but some don't
for this situation, usually use find command to locate it
I recently install the vim-doc
but I don't know where those html file installed
I even can't find them through find

any good ideas?

thx,

David

---

### Post by oldos2er on 2010-01-03
```
dpkg -L vim-doc
``` will show you where the files in the package are installed.

---

### Post by tanyeun on 2010-01-03
thx, that works great!
what about those program I install from the source code?

---

### Post by jonest1 on 2010-01-03
If you install via source code, you usually specify the prefix and they usually default to the /usr/local filesystem.  Run the following to get a list of options and the defaults from the configure script.

```
./configure --help
```

This assumes the source is setup with the typical configure, make, make install compilation scenario.

---

