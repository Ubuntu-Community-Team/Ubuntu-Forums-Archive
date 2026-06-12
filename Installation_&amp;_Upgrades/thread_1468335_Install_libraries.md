---
title: "Install libraries"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by NorthDakota91 on 2010-05-01
Hi all! Yesterday I have downloaded the new Ubuntu Lucid x64. I'm trying to install my Canon Pixma MP270 printer. The drivers provided by Canon aren't working with 64bit systems so I decided to try to compile the drivers from sources. The compilation requires these libraries:

```

    * libm         (6.0    or above)
    * libdl        (2.0    or above)
    * libpopt      (1.4    or above)
    * libcnclapi   (3.1.0  or above)
    * libcnclbjcmd (3.1.0  or above)
    * libcnclui    (3.1.0  or above)
    * libcnbpess   (2.0.5  or above)
    * libcnbpcmcm  (6.11.1 or above)
    * libcnbpoxxx  (1.0.x  or above)
    * libtiff      (3.4    or above)
    * libpng       (1.0.9  or above)

```

The question is: how can I install these libraries? I've tried to search them with the software center and apt-get with no luck. So where can I get these libs? (Sorry for a noob question but I have just no idea on where to look..)

Thank you! :)

---

### Post by svinx on 2010-09-12
bump :)

Are there equivalent deb packages?

---

### Post by robbiemacg on 2010-09-12
You should be able to install these libraries via Synaptic Package Manager with no muss and no fuss.
System >Administration >Synaptic Package Manager

---

