---
title: "How can I replace a shared library with a newer version (compiled from source)?"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by TnT001 on 2006-08-05
Is it possible to replace a shared library (libexif) with my own version, compiled from source? When I go through the normal "./configure && make && make install" procedure, everything gets installed to /usr/lib/local. But the old version remains on my system and all applications (like eog and gthumb) are still using the old version. In synaptic, I can't remove libexif, without removing those applications also. Is there a way to change that?

---

### Post by droogy on 2006-08-28
I too would like to know the answer to this... anyone?

---

### Post by TnT001 on 2006-08-30
I also posted my question in the newsgroup alt.os.linux and got some replies there. But I'm still having trouble with it.

[http://groups.google.com/group/alt.os.linux/browse_thread/thread/582acc43f7e0fbca/019022f250170e50](http://groups.google.com/group/alt.os.linux/browse_thread/thread/582acc43f7e0fbca/019022f250170e50)

---

### Post by TnT001 on 2006-09-20
I found some very useful information in the debian apt howto. Section 4.1 explains how to create a fake package that takes care of dependencies and makes it possible to remove the original package:

[http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs](http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs)

Section 6 is explains how to build debian packages from source (and the possibility to patch before building). Now I only need to find a way to update the debian source to the one in cvs.

---

