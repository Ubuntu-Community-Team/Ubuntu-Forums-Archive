---
title: "Cannot install downloaded package"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by pepribal on 2013-03-02
I've downloaded a 32-bit deb package which installs well in my ubuntu boxes. However in one of them I get an error all the time. When I try to install it, ubuntu says it cannot proceed because the package is requesting to remove an essential package called 'base-files'. How can I fix it?

Thanks.

---

### Post by tgalati4 on 2013-03-02
My mind-reading skills are weak today.  What package were you trying to install?  Are you sure all of the machines are 32-bit?

tgalati4@Mint14-Extensa ~ $ apt-cache depends base-files
base-files
  PreDepends: <awk>
    gawk:i386
    gawk
    original-awk
    mawk:i386
    mawk
  Breaks: initscripts
  Breaks: initscripts:i386
  Replaces: <base>
    base-files
  Replaces: <base:i386>
    base-files:i386
  Replaces: dpkg
  Replaces: dpkg:i386
  Replaces: lsb-release
  Replaces: <lsb-release:i386>
  Replaces: <miscutils>
  Replaces: <miscutils:i386>
  Conflicts: base-files:i386

---

### Post by pepribal on 2013-03-03
It's a software by a VPN services provider (Astrill). I assumed it would be something not well configured in my linux box.

Anyway, you were right: it was a 64-bit system. I tried the 64-bit package, and it worked. I thought 32-bit packages would work in 64-bit systems, but obviously I was wrong.

Sorry 'bout that.

---

