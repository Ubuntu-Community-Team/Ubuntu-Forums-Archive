---
title: "fotoxx install error"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-23
I'm trying to install an image program called fotoxx from a .deb file. It installs fine on jaunty. Here is the error message I get in the terminal when trying to install in karmic:

Setting up libfreeimage3 (3.10.0-1)...

Processing triggers for libc-bin... ldconfgi deferred processing now taking place
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor


Any ideas?

---

### Post by kornelix on 2009-09-29
Packages on the fotoxx web site were built with Ubuntu 8.4 and will install on 8.4, 8.10, and 9.04 but not on 9.10. I don't know why and will dig into this later. For now, I suggest you build from the source tarball as explained on the fotoxx web site. That works OK for 9.10.
(from author of fotoxx)

---

### Post by oboedad55 on 2009-09-29
> **kornelix said:**
> Packages on the fotoxx web site were built with Ubuntu 8.4 and will install on 8.4, 8.10, and 9.04 but not on 9.10. I don't know why and will dig into this later. For now, I suggest you build from the source tarball as explained on the fotoxx web site. That works OK for 9.10.
(from author of fotoxx)

Actually, I finally got the .deb file to work on karmic. I'm not sure what I did but I think it was like dpkg -f.

---

### Post by cariboo on 2009-09-29
I installed fotoxx yesterday, gebi wouldn't install it, I had to use dpkg -i to install it after the dependencies were met.

---

