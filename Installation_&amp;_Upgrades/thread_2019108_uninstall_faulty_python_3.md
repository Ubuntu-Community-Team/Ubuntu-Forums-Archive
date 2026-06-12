---
title: "uninstall faulty python 3"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by locomonkey on 2012-07-07
I downloaded and installed python 3 using configure and makefiles (none of which I really understand) rather than **apt-get** and although the interpreter worked fine, it didn't come with all the modules I wanted. In the course of trying to uninstall it I went a little crazy deleting the directory that I configured it in, and managed to delete the install.txt and the makefile. Now, when I use **apt-get remove** I get the following nasty-looking error:

```
(Reading database ... 181016 files and directories currently installed.)
Removing python3 ...
/var/lib/dpkg/info/python3.prerm: 4: /var/lib/dpkg/info/python3.prerm: py3clean: not found
dpkg: error processing python3 (--remove):
 subprocess installed pre-removal script returned error exit status 127
/var/lib/dpkg/info/python3.postinst: 47: /var/lib/dpkg/info/python3.postinst: py3compile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 python3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I repent of my over-eager, arrogant ways, I just want to be able to uninstall it and install a fresh version!

---

### Post by sanderj on 2012-07-07
Yes, that's why "sudo apt-get install" is much preferred over "configure, make, make install". 

Maybe a

```

sudo apt-get install python3

sudo apt-get remove python3
```

helps. If not, I would reinstall Unbuntu.

---

