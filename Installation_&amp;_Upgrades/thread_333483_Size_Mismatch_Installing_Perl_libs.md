---
title: "Size Mismatch Installing Perl libs"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by Tim Sawyer on 2007-01-07
Hi,

I'm trying to install slimserver from [http://debian.slimdevices.com](http://debian.slimdevices.com), but I'm having trouble getting some of the needed perl libs onto my system.  I'm running edubunutu 6.10, with kubuntu-desktop installed.  The offending libs are:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/libs/libsql-abstract-perl/libsql-abstract-perl_1.21-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/libs/libsql-abstract-perl/libsql-abstract-perl_1.21-1_all.deb)  Size mismatch

How can I get these to work?  It seems that my system thinks that they are a different size to what they are, is this a repository problem?

ta,

Tim.

---

### Post by 23meg on 2007-01-07
Why don't you install it from the Ubuntu repositories? It's in Universe.

---

### Post by Tim Sawyer on 2007-01-07
Hmm.  It installs, but it's version 6.2.1 where the latest (which I was using successfully on edgy amd64 before I decided to re-install i386) is version 6.5.  Not sure what my squeezebox will make of it, have to wait and see....

Tim.

---

### Post by Tim Sawyer on 2007-01-09
The squeezebox wants to downgrade the firmware, and I don't really want to let it do that, after the trouble I had last time.

Is the perl libs problem a repository problem?  What do I do to get it fixed?

Tim.

---

