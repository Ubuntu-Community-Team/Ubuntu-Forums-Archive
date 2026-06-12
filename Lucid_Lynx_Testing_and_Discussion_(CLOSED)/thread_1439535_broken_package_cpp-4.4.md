---
title: "broken package cpp-4.4"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nanog on 2010-03-26
```
Unpacking replacement cpp-4.4 ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/cpp-4.4_4.4.3-4ubuntu4_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/gcc/x86_64-linux-gnu/4.4/cc1')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-4.4_4.4.3-4ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

"dpkg --configure -a" and "apt-get install -f" fail.

---

### Post by nanog on 2010-03-26
This is serious breakage. I may have to hack at dpkg to fix this.

```
$ sudo dpkg --force-remove-reinstreq -r cpp-4.4
dpkg: dependency problems prevent removal of cpp-4.4:
 cpp depends on cpp-4.4 (>= 4.4.3-1).
dpkg: error processing cpp-4.4 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 cpp-4.4
```

---

### Post by nanog on 2010-03-26
sudo apt-get remove --purge gcc-4.4 (a dependency of cpp-4.4) worked. unfortunately it also removed X and ubuntu-desktop. reinstall of ubuntu-desktop is now broken because of cpp-4.4 (which caused a cascade of dependency errors).

---

### Post by nanog on 2010-03-26
cached package was the problem. when deleted (rm /var/cache/apt/archives/cpp-4.4_4.4.3-4ubuntu4_amd64.deb) upgrade proceeded normally.

---

