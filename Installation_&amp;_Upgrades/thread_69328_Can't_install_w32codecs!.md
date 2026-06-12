---
title: "Can't install w32codecs!"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by St3althcAt on 2005-09-26
Hello all!
Well, I've installed Ubuntu some times and this time, I had a problem with both Windows and Linux, ended with errors on Grub... Well a total mess :P!
I've reinstalled Ubuntu but now when I'm going to install the w32codecs, following, as always, the Ubuntu Guide, I get this error on the terminal:

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I really would like to have those codecs, you know? Any help would be welcome!

Thank you for your attention!

---

### Post by Leif on 2005-09-26
add deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main to your sources. w32codecs has been removed from the backports.

---

