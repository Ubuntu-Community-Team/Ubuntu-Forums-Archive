---
title: "ia32-libs package is broken!"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2008-10-31
I've tried to install the ia32-libs package for 8.10 from several redepositors and the package is broken.  what can I do to get this installed?  

Jose

---

### Post by Partyboi2 on 2008-11-01
What is the error message you are getting when you try and install the package?

---

### Post by cybergalvez on 2008-11-01
> **Partyboi2 said:**
> What is the error message you are getting when you try and install the package?

here is the error:

Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu18_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cybergalvez on 2008-11-03
Interesting, I updated my nvidia driver from version 173 to 177 and now ia32-libs installs.  
Jose

---

