---
title: "Unable to install Funguloids"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by leviathan8 on 2011-01-25
Hello... been trying to install this game months ago... and I still can't do it. I tried from the command line, software center, synaptic, compiling and it still won't work. This is what I get when I run the install from cli:

> mono@mono-laptop:~$ sudo apt-get install funguloids
[sudo] password for mono: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  funguloids: Depends: ogre-plugins-cgprogrammanager but it is not installable
E: Broken packages
I understand that this package is missing... but I have no idea how to install the dependency.

---

### Post by directhex on 2011-01-25
> **leviathan8 said:**
> Hello... been trying to install this game months ago... and I still can't do it. I tried from the command line, software center, synaptic, compiling and it still won't work. This is what I get when I run the install from cli:

I understand that this package is missing... but I have no idea how to install the dependency.

apt-get install ogre-plugins-cgprogrammanager ?

---

### Post by leviathan8 on 2011-01-26
> **directhex said:**
> apt-get install ogre-plugins-cgprogrammanager ?

Nope.

> nubuntu@nubuntu-desktop:~$ sudo apt-get install ogre-plugins-cgprogrammanager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ogre-plugins-cgprogrammanager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ogre-plugins-cgprogrammanager has no installation candidate


---

### Post by directhex on 2011-01-26
> **leviathan8 said:**
> Nope.

You have Multiverse enabled?

You're on Maverick or above?

---

### Post by IWantFroyo on 2011-01-26
Maybe you should try getting Aptitude from the software center. It isn't as good, but it might have a funguloids download that works.

---

### Post by leviathan8 on 2011-01-26
I managed to install the OGRE package, but now I am stuck up with an error while compiling.

```
nubuntu@nubuntu-desktop:~/Downloads/funguloids$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for int32_t... yes
checking for size_t... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether closedir returns void... no
checking for error_at_line... yes
checking for working memcmp... yes
checking for memmove... yes
checking for memset... yes
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OGRE... yes
configure: Ogre plugins found in /usr/lib/OGRE
checking for OIS... yes
checking lua.h usability... no
checking lua.h presence... no
checking for lua.h... no
checking for lua.h library with -I/usr/local/include/lua5.1... no
checking for lua.h library with -I/usr/local/include/lua... no
checking for lua.h library with -I/usr/local//... no
checking for lua.h library with -I/usr/include/lua5.1... no
checking for lua.h library with -I/usr/include/lua... no
checking for lua.h library with -I/usr//... no
checking for LUA... no
checking for LUA... no
configure: error: Lua 5.1 not found. You can specify its location with --with-lua=/path/to/include/lua51

```

I have lua5.1 installed in /usr/bin but even adding --with-lua=/usr/bin/lua5.1 doesn't help. Any ideas?

---

### Post by leviathan8 on 2011-01-26
I managed to install all the dependencies and the game itself (using .deb packages from this[ link]("http://packages.ubuntu.com/lucid/i386/funguloids/download") and [this]("http://packages.ubuntu.com/lucid/i386/libogremain-1.6.4/download")), however the game will just crash on startup... Guess I'll just drop it.

---

### Post by lainme on 2011-02-11
> **leviathan8 said:**
> I managed to install the OGRE package, but now I am stuck up with an error while compiling.

```
nubuntu@nubuntu-desktop:~/Downloads/funguloids$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for int32_t... yes
checking for size_t... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether closedir returns void... no
checking for error_at_line... yes
checking for working memcmp... yes
checking for memmove... yes
checking for memset... yes
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OGRE... yes
configure: Ogre plugins found in /usr/lib/OGRE
checking for OIS... yes
checking lua.h usability... no
checking lua.h presence... no
checking for lua.h... no
checking for lua.h library with -I/usr/local/include/lua5.1... no
checking for lua.h library with -I/usr/local/include/lua... no
checking for lua.h library with -I/usr/local//... no
checking for lua.h library with -I/usr/include/lua5.1... no
checking for lua.h library with -I/usr/include/lua... no
checking for lua.h library with -I/usr//... no
checking for LUA... no
checking for LUA... no
configure: error: Lua 5.1 not found. You can specify its location with --with-lua=/path/to/include/lua51

```

I have lua5.1 installed in /usr/bin but even adding --with-lua=/usr/bin/lua5.1 doesn't help. Any ideas?

install liblua5.1-dev

---

