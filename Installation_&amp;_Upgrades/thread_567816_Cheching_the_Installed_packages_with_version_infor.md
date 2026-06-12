---
title: "Cheching the Installed packages with version information"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by shoaibnawaz on 2007-10-05
I am new to Ubuntu. In a short time I learned the way to install packages on Ubuntu. Although I am software developer, I always find the tools libraries. I came to know that GCC compiler is always shipped with every distro of Linux. How can I check it on my system. I mean what is the terminal command regarding "apt-get" to get the information about a specific package or viewing the list of all installed packages.

Please guide me in this regard.

---

### Post by elvis on 2007-10-05
"apt" is a front end for "dpkg".  dpkg contains all the information you need about installed versions.

"man dpkg" of course will give you everything it does, but what you're after in particular is "dpkg -l" (lower case L) which will "list" the packages installed.  Use grep to filter out what interests you.

For instance, on my Gutsy machine:

```

dan@danmobile:~$ dpkg -l | grep gcc
ii  gcc                                        4:4.1.2-9ubuntu2                     The GNU C compiler
ii  gcc-3.3-base                               1:3.3.6-15ubuntu2                    The GNU Compiler Collection (base package)
ii  gcc-3.4-base                               3.4.6-6ubuntu2                       The GNU Compiler Collection (base package)
ii  gcc-4.1                                    4.1.2-16ubuntu2                      The GNU C compiler
ii  gcc-4.1-base                               4.1.2-16ubuntu2                      The GNU Compiler Collection (base package)
ii  gcc-4.2-base                               4.2.1-5ubuntu4                       The GNU Compiler Collection (base package)
ii  libgcc1                                    1:4.2.1-5ubuntu4                     GCC support library
dan@danmobile:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```

"dpkg -l | grep gcc" shows me all of the GCC versions installed locally.  There's a few there, so to check which is currently default, "gcc -v" tells me the version of the first "gcc" executable in my path.

---

