---
title: "[SOLVED] Can not install packages"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Kognit on 2008-05-06
I am trying to install a program gshutdown-0.2 from a source. I tried to configure and this came out: 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for library containing strerror... none required
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for /proc/self/maps... yes
checking whether everything is installed to the same prefix... no
checking whether binary relocation support should be enabled... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0
             glib-2.0 >= 2.6
             libglade-2.0 >= 2.0.0
             libnotify >= 0.3.2) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'libglade-2.0' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Allriht, i said. I will mannualy install the packages. I wrote ```
sudo apt-get intall gtk+-2.0
```, and then get it ```
E: Invalid operation intall
```

Then i tried to install the other package ```
sudo apt-get install libgtk-2.0
```
and get this ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-2.0
``` 

Can anyone help me?

---

### Post by fixitdude on 2008-05-06
You probably want to use the synaptic package manager to install stuff (if it's not installed then do so). It's easier when looking for stuff you don't know what the exact name is.

You probably just want gtk and glib (not "gtk+-2.0"), but look for "dev" packages with those names, I think that's mostly what you need.

If you don't find any "dev" files (it will say something like "name-dev") then maybe you don't have the development repositories enabled.

Make sure gcc, gdb and g++ are installed too.

---

### Post by jw5801 on 2008-05-06
> **fixitdude said:**
> You probably want to use the synaptic package manager to install stuff (if it's not installed then do so). It's easier when looking for stuff you don't know what the exact name is.

You probably just want gtk and glib (not "gtk+-2.0"), but look for "dev" packages with those names, I think that's mostly what you need.

If you don't find any "dev" files (it will say something like "name-dev") then maybe you don't have the development repositories enabled.

Make sure gcc, gdb and g++ are installed too.

```
sudo aptitude install libgtk2.0-dev libglade2-dev libnotify-dev
```

Usually if you're trying to compile something you'll need the relevant -dev packages, use sudo aptitude seach "blah", or synaptic to search for them.

---

### Post by Kognit on 2008-05-06
i did ```
 sudo aptitude install libgtk2.0-dev libglade2-dev libnotify-dev 
``` and works. Thanks

---

### Post by jw5801 on 2008-05-06
No dramas! Dependencies are a pain until you start learning where to look.

---

### Post by ripgut on 2008-05-06
On the first, you spelled **intall** instead of install.

---

