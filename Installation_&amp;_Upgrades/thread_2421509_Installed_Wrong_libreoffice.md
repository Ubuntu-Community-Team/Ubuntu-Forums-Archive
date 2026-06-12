---
title: "Installed Wrong libreoffice"
date: 2019-06-22
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2019-06-22
My Ubuntu install (16.04) came with libreoffice 5. I wanted to upgrade to libreoffice 6, so I went to the libreoffice site and downloaded all the debs, but I should have downloaded the 64 bit version and didn't (stupid me!). It won't run - it returns "/opt/libreoffice6.2/program/oosplash: error while loading shared libraries: libXinerama.so.1: wrong ELF class: ELFCLASS64"

So I tried removing it, and here's what sudo dpkg -r libreoffice6.2 returns:
```

dpkg: dependency problems prevent removal of libreoffice6.2:i386:
 libreoffice6.2-dict-en:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-dict-en:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-dict-en:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-dict-en:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-base:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-base:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-base:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-base:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-impress:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-impress:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-impress:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-impress:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).
 libreoffice6.2-calc:i386 depends on libreoffice6.2 (>= 6.2.4.2).
 libreoffice6.2-calc:i386 depends on libreoffice6.2 (<= 6.2.4.2-2).

```

Some advice would be appreciated. Can I install the 64 bit version without deleting the one installed? I've tried removing the packages one at a time but I'm getting unspecified dependency problems there too.

---

### Post by TheFu on 2019-06-22
This article [http://ubuntuhandbook.org/index.php/2019/03/libreoffice-6-2-available-install-ppa/](http://ubuntuhandbook.org/index.php/2019/03/libreoffice-6-2-available-install-ppa/)
explains to use a PPA for libreoffice.  v6.2 is available.

For any lurkers, .deb files tend to break other dependencies in a few months.  Everything is fine initially, but slowly, apt-get upgrade fails.  Now the system has broken package dependencies.

---

### Post by bilkay on 2019-06-23
Thanks for the response. 

Using dpkg -r on all the packages, I was able to remove all but libreoffice6.2-ure:i386 and libobasis6.2-core. The problems are libobasis6.2-core depends on libreoffice6.2-ure, and libobasis6.2-extension-nlpsolver depends on libobasis6.2-core. I have no idea where libobasis6.2-extension-nlpsolver came from.

---

### Post by TheFu on 2019-06-23
I haven't used dpkg to install or remove anything in about a decade.  It just isn't something we do.  Using the new 'apt' front-end should handle dependencies better, in theory, for .deb file installs.  Regardless, it is best to avoid directly installing .deb files.

Remove them all, including whatever libreoffice stuff you have. Then go back and use the PPA method.

---

