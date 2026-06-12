---
title: "Problem on installing iscan-2.8.0-1.c2.tar.gz"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by satimis on 2007-08-10
Hi folks,

Ubuntu 7.04 desktop
Epsonperfection 3490 Photo -scanner


Tried to install iscan-2.8.0-1.c2.tar.gz, the software developed by Epson, encounting following problem;

After extraction;

$ cd iscan-2.8.0/
$ su
# ./configure```

....
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

# cat config.log```

....
configure:1574: checking for a BSD-compatible install
configure:1629: result: /usr/bin/install -c
configure:1640: checking whether build environment is sane
configure:1683: result: yes
configure:1748: checking for gawk
configure:1777: result: no
configure:1748: checking for mawk
configure:1764: found /usr/bin/mawk
configure:1774: result: mawk
configure:1784: checking whether make sets $(MAKE)
configure:1804: result: yes
configure:2027: checking for g++
configure:2056: result: no
configure:2027: checking for c++
configure:2056: result: no
configure:2027: checking for gpp
configure:2056: result: no
configure:2027: checking for aCC
configure:2056: result: no
configure:2027: checking for CC
configure:2056: result: no
configure:2027: checking for cxx
configure:2056: result: no
configure:2027: checking for cc++
configure:2056: result: no
configure:2027: checking for cl
configure:2056: result: no
configure:2027: checking for FCC
configure:2056: result: no
configure:2027: checking for KCC
configure:2056: result: no
configure:2027: checking for RCC
configure:2056: result: no
configure:2027: checking for xlC_r
configure:2056: result: no
configure:2027: checking for xlC
configure:2056: result: no
configure:2069: checking for C++ compiler version
configure:2072: g++ --version </dev/null >&5
./configure: line 2073: g++: command not found
configure:2075: $? = 127
configure:2077: g++ -v </dev/null >&5
./configure: line 2078: g++: command not found
configure:2080: $? = 127
configure:2082: g++ -V </dev/null >&5
./configure: line 2083: g++: command not found
configure:2085: $? = 127
configure:2108: checking for C++ compiler default output file name
configure:2111: g++    conftest.cc  >&5
./configure: line 2112: g++: command not found
configure:2114: $? = 127
configure: failed program was:
| /* confdefs.h.  */
....

```

$ apt-cache policy gcc```

gcc:
  Installed: 4:4.1.2-1ubuntu1
  Candidate: 4:4.1.2-1ubuntu1
  Version table:
 *** 4:4.1.2-1ubuntu1 0
        500 http://hk.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```
Already installed.

$ apt-cache policy c++
W: Unable to locate package c++
$ apt-cache policy C++
W: Unable to locate package C++
$ apt-cache policy gcc-c++
W: Unable to locate package gcc-c++
$ apt-cache policy gcc-C++
W: Unable to locate package gcc-C++

$ apt-cache policy g++```

g++:
  Installed: (none)
  Candidate: 4:4.1.2-1ubuntu1
  Version table:
     4:4.1.2-1ubuntu1 0
        500 http://hk.archive.ubuntu.com feisty/main Packages

```
Not installed yet.


Please advise where can I get C++ ?  
Whether I need to install g++ ??

TIA


B.R.
satimis

---

### Post by PaulFr on 2007-08-10
Perhaps you want to install **build-essential** which installs both gcc, g++, make and dpkg.

---

### Post by satimis on 2007-08-10
> **PaulFr said:**
> Perhaps you want to install **build-essential** which installs both gcc, g++, make and dpkg.
Hi PaulFr,

$ sudo apt-get install build-essential```

....
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...


```
Went through w/o complaint.


# ./configure ```

....
.....
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking C++ ABI version... 1002
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... checking for gtk+... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
yes
checking GTK_CFLAGS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking GTK_LIBS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking for imlibgdk... Package imlibgdk was not found in the pkg-config search path. Perhaps you should add the directory containing `imlibgdk.pc' to the PKG_CONFIG_PATH environment variable No package 'imlibgdk' found
configure: error: Library requirements (imlibgdk) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
Still failed.


# apt-cache policy pkg-config```

pkg-config:
  Installed: 0.21-1build1
  Candidate: 0.21-1build1
  Version table:
 *** 0.21-1build1 0
        500 http://hk.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```
Already installed.

# apt-cache policy imlibgdk
W: Unable to locate package imlibgdk
# apt-cache policy gtk+-2.0
W: Unable to locate package gtk+-2.0

They can't be found.


B.R.
satimis

---

### Post by PaulFr on 2007-08-10
I would suggest ```
sudo apt-get install libgtk2.0-dev libgtkglext1-dev
```Also, please use **aptitude search <part_of_package_name>**to search for packages - it will give you a one line description of the package. **aptitude show <package_name>** will give you a detailed description including installation status and dependencies.

---

### Post by satimis on 2007-08-10
> **PaulFr said:**
> I would suggest ```
sudo apt-get install libgtk2.0-dev libgtkglext1-dev
```

$ sudo apt-get install libgtk2.0-dev libgtkglext1-dev
Went through w/o complaint

$ cd /iscan-2.8.0
$ su
# ./configure

It also went through w/o complaint

# make```

......
....
In file included from imgstream.cc:31:
imgstream.hh:46:18: error: ltdl.h: No such file or directory
imgstream.hh:115: error: ‘lt_dlhandle’ does not name a type
imgstream.hh:116: error: ‘lt_ptr’ does not name a type
imgstream.hh:118: error: ‘dl_handle’ does not name a type
imgstream.hh:120: error: ‘dl_ptr’ does not name a type
imgstream.hh:121: error: ‘dl_handle’ has not been declared
imgstream.hh:124: error: ‘dl_handle’ does not name a type
imgstream.cc:155: error: ‘dl_handle’ in class ‘iscan::imgstream’ does not name a type
imgstream.cc:174: error: ‘dl_ptr’ in class ‘iscan::imgstream’ does not name a type
imgstream.cc:181: error: ‘int iscan::imgstream::dlclose’ is not a static member of ‘class iscan::imgstream’
imgstream.cc:181: error: ‘dl_handle’ was not declared in this scope
imgstream.cc:182: error: expected ‘,’ or ‘;’ before ‘{’ token
imgstream.cc:211: error: ‘dl_handle’ in class ‘iscan::imgstream’ does not name a type
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/satimis/iscan-2.8.0'
make: *** [all] Error 2

```
stuck here.

> 
Also, please use **aptitude search <part_of_package_name>**to search for packages - it will give you a one line description of the package. **aptitude show <package_name>** will give you a detailed description including installation status and dependencies.
$ sudo aptitude update
$ aptitude search imlibgdk
$ aptitude show imlibgdk
E: Unable to locate package imlibgdk
$ aptitude show imlibgdk.pc
E: Unable to locate package imlibgdk.pc
$ aptitude show imlibgdk.pc
E: Unable to locate package imlibgdk.pc
$ aptitude show gtk-config
E: Unable to locate package gtk-config
$ aptitude search gtk-config
$ aptitude search GTK_CFLAGS
$ sudo aptitude search GTK_CFLAGS
Password:
No printout
$ sudo aptitude search GTK_CFLAGS
$ aptitude search GTK_CFLAGS
$ man aptitude
$ aptitude show imlibgdk
E: Unable to locate package imlibgdk
satimis@ubuntu704:~$ aptitude search imlibgdk

Did I miss something?  Tks


B.R.
satimis

---

### Post by PaulFr on 2007-08-10
AFAICS, imlibgdk is not your problem. Look at your first error. ltdl.h is missing. ltdl.h is included in libltdl3-dev. Please install it using ```
sudo apt-get install libltdl3-dev
```BTW, aptitude show <package_name> has to have the exact package name, whereas aptitude search <part_of_package_name> will search for the string inside the package name and summary. So for example, **aptitude search ltdl** will give you three packages one of which is libltdl3-dev. Now running **aptitude show libltdl3-dev** will give you details about this package. No point in running **aptitude show ltdl** or **aptitude show imlibgdk** since ltdl or imlibgdk are not exact package names.

---

### Post by satimis on 2007-08-11
Hi PaulFr,

> 
AFAICS, imlibgdk is not your problem. Look at your first error. ltdl.h is missing. ltdl.h is included in libltdl3-dev. Please install it using ```
sudo apt-get install libltdl3-dev
```


$ sudo apt-get install libltdl3-dev
went throught w/o complaint

$ cd iscan-2.8.0
$ su
# ./configure
Also went through w/o complaint

# make```

...
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -I../include -g -O2 -MT libsanei_la-sanei_config.lo -MD -MP -MF .deps/libsanei_la-sanei_config.Tpo -c sanei_config.c  -fPIC -DPIC -o .libs/libsanei_la-sanei_config.o
In file included from sanei_config.c:52:
../include/sane/sanei.h:89:23: error: sane/sane.h: No such file or directory
In file included from sanei_config.c:52:
../include/sane/sanei.h:163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sanei_check_value’
../include/sane/sanei.h:166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sanei_constrain_value’
In file included from sanei_config.c:53:
../include/sane/sanei_config.h:124: error: expected declaration specifiers or ‘...’ before ‘SANE_Status’
sanei_config.c: In function ‘sanei_config_get_string’:
sanei_config.c:166: warning: incompatible implicit declaration of built-in function ‘strndup’
make[2]: *** [libsanei_la-sanei_config.lo] Error 1
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/sanei'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/satimis/iscan-2.8.0'
make: *** [all] Error 2

```
It is now stuck here.

$ sudo find / -name sane.h
No printout

$ sudo find / -name sanei.h```

/home/satimis/iscan-2.8.0/include/sane/sanei.h

```
"sanei.h" found

> 
BTW, aptitude show <package_name> has to have the exact package name, whereas aptitude search <part_of_package_name> will search for the string inside the package name and summary. So for example, **aptitude search ltdl** will give you three packages one of which is libltdl3-dev. Now running **aptitude show libltdl3-dev** will give you details about this package. No point in running **aptitude show ltdl** or **aptitude show imlibgdk** since ltdl or imlibgdk are not exact package names.
Noted with tks.


On aptitude and apt-get, are there ways finding the packages which provide dep?


B.R.
satimis

---

### Post by PaulFr on 2007-08-11
The error is sane.h is missing ```
../include/sane/sanei.h:89:23: error: sane/sane.h: No such file or directory
``` So **aptitude search sane** gives you two -dev libraries - libsane-dev and libsane-extras-dev. I would suggest you install lbsane-dev first ```
sudo apt-get libsane-dev
``` and try to compile and see if you get any further errors. The libsane-extras-dev are for some specific scanners and you may not need it.> On aptitude and apt-get, are there ways finding the packages which provide dep?Yes, of course, if you had a standard Ubuntu package, the dependencies are inside the .deb and so when you try to install it, it will install the dependencies also without any problem. For example, **aptitude show libsane-dev** shows dependencies on libsane, libusb-dev, libjpeg62-dev, libtiff4-dev, libieee1284-dev. All these will be checked for and installed if not already present, when you install libsane-dev.

But you are trying to compile from source, and here you are dependent on the documentation in the package. I would have expected the Epson developers to indicate a list of libraries or packages they required. Sans that, we have to keep at it till we get it working.

But one more useful tool for you : ```
sudo apt-get apt-file
``` This will help you find what packages may carry a file. So you could run ```
apt-file search sane.h
``` and it would give you three packages of which only one libsane-dev contains sane.h (the others are for sane.html).

---

### Post by satimis on 2007-08-12
Hi PaulFr,


$ sudo apt-get install libsane-dev
went through w/o complaint

$ cd iscan-2.8.0
$ su
# ./configure
Also went through w/o complaint


# make```

....
.....
Making all in utils
make[2]: Entering directory `/home/satimis/iscan-2.8.0/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/utils'
Making all in po
make[2]: Entering directory `/home/satimis/iscan-2.8.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/po'
Making all in intl
make[2]: Entering directory `/home/satimis/iscan-2.8.0/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/intl'
Making all in non-free
make[2]: Entering directory `/home/satimis/iscan-2.8.0/non-free'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/non-free'
Making all in doc
make[2]: Entering directory `/home/satimis/iscan-2.8.0/doc'
Generating manpage iscan.1...
Generating manpage sane-epkowa.5...
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/doc'
make[2]: Entering directory `/home/satimis/iscan-2.8.0'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0'
make[1]: Leaving directory `/home/satimis/iscan-2.8.0'

```

# make install```

....
test -z "/usr/local/man/man5" || mkdir -p -- "/usr/local/man/man5"
 /usr/bin/install -c -m 644 './sane-epkowa.5' '/usr/local/man/man5/sane-epkowa.5'
make[2]: Leaving directory `/home/satimis/iscan-2.8.0/doc'
make[1]: Leaving directory `/home/satimis/iscan-2.8.0/doc'
make[1]: Entering directory `/home/satimis/iscan-2.8.0'
make[2]: Entering directory `/home/satimis/iscan-2.8.0'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/satimis/iscan-2.8.0'
make[1]: Leaving directory `/home/satimis/iscan-2.8.0'

```

Seems OK

$ iscan```

iscan: error while loading shared libraries: libesmod.so.1: cannot open shared object file: No such file or directory

```

$ sudo ldconfig
No complaint

$ iscan```

iscan: error while loading shared libraries: libesmod.so.1: cannot open shared object file: No such file or directory

```
Still the same.

$ sudo find / -name libesmod.so.1```

/usr/local/lib/libesmod.so.1

```
What shall I do?  Tks.


> 
But one more useful tool for you : ```
sudo apt-get apt-file
``` This will help you find what packages may carry a file. So you could run ```
apt-file search sane.h
``` and it would give you three packages of which only one libsane-dev contains sane.h (the others are for sane.html).
This is the tool I'm looking for.  Yum has similar operation.

$ sudo apt-get install apt-file
went through w/o complaint.

$ which apt-file
/usr/bin/apt-file

$ apt-file search/show/list sane.h
all w/o printout.


B.R.
satimis

---

### Post by PaulFr on 2007-08-12
Please add /usr/local/lib to the list of directories to scan for libraries: ```
sudo -s
echo /usr/local/lib >> /etc/ld.so.conf
/sbin/ldconfig
exit
```Now try iscan.

It's curious how you get no output when running apt-file search sane.h - here is my output: ```
doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
libsane-dev: usr/include/sane/sane.h
```Can you check if you have source repositories turned on in Synaptic ? To do this (I assume you have a gnome desktop),
1. Click System on top, then Administration, then Synaptic Package Manager. After entering your password, the package management application comes up.
2. In that application, select the Settings menu, and in that select Repositories - a dialog will come up which has a list of repository types (I've attached a screen snapshot of my settings).
3. Please mark the types of repositories, but do make sure the Source checkbox is checked.
4. After clicking Close to dismiss this dialog, close the application.
5. Now in a terminal run ```
sudo apt-get update
sudo apt-get upgrade
apt-file search sane.h
```Do you get any output ? BTW, the first line in the above is to update the information for all packages whereas the second line (sudo apt-get upgrade) is for upgrading your system.

---

### Post by satimis on 2007-08-12
> **PaulFr said:**
> Please add /usr/local/lib to the list of directories to scan for libraries: ```
sudo -s
echo /usr/local/lib >> /etc/ld.so.conf
/sbin/ldconfig
exit
```Now try iscan.

Performed following steps;

$ sudo -s
Password:
# echo /usr/local/lib >> /etc/ld.so.conf
# /sbin/ldconfig
Both w/o complaint
 
# exit
exit

$ iscan

A warning popup```

Could not send command to scanner
Check the scanner's status

```

$ scanimage -T```

[snapscan] Scanner warming up - waiting 8 seconds.
scanimage: scanning image of size 2552x3507 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 7656 bytes...  PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 2048 bytes...  PASS
scanimage: stepped read, 4096 bytes...  PASS
scanimage: stepped read, 8192 bytes...  PASS
scanimage: stepped read, 8191 bytes...  PASS
scanimage: stepped read, 4095 bytes...  PASS
scanimage: stepped read, 2047 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

```
Scanner communicated.


> 
It's curious how you get no output when running apt-file search sane.h - here is my output: ```
doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
libsane-dev: usr/include/sane/sane.h
```Can you check if you have source repositories turned on in Synaptic ? To do this (I assume you have a gnome desktop),
1. Click System on top, then Administration, then Synaptic Package Manager. After entering your password, the package management application comes up.
2. In that application, select the Settings menu, and in that select Repositories - a dialog will come up which has a list of repository types (I've attached a screen snapshot of my settings).
3. Please mark the types of repositories, but do make sure the Source checkbox is checked.
4. After clicking Close to dismiss this dialog, close the application.
5. Now in a terminal run ```
sudo apt-get update
sudo apt-get upgrade
apt-file search sane.h
```Do you get any output ? BTW, the first line in the above is to update the information for all packages whereas the second line (sudo apt-get upgrade) is for upgrading your system.
Found "Source code" not checked.

Check "Source Code" --> Reload --> Close

On Terminal;

$ sudo apt-get update
No complaint

$ sudo apt-get upgrade```

.....
Hit http://wine.budgetdedicated.com edgy/main Packages
Fetched 8B in 1m40s (0B/s)
Reading package lists... Done
satimis@ubuntu704:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives.
After unpacking 1907kB of additional disk space will be used.
Do you want to continue [Y/n]? n

```
I don't want to upgrade "wine" for the time being.


$ apt-file search sane.h
Still no printout


B.R.
satimis

---

### Post by PaulFr on 2007-08-12
So you still cannot find sane.h - curious. Maybe some one else can help here.

---

### Post by satimis on 2007-08-13
> **PaulFr said:**
> So you still cannot find sane.h - curious. Maybe some one else can help here.
Hi PaulFr,


This time it worked

$ sudo apt-file update
It took prolonged time to finish working on background

$ sudo apt-file search sane.h```

doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-html: usr/share/doc/HOWTO/en-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/Scanner-HOWTO/sane.html
libsane-dev: usr/include/sane/sane.h
libsane-dev: usr/include/sane/sane.h
libsane-dev: usr/include/sane/sane.h
libsane-dev: usr/include/sane/sane.h

```
Instead of printing out once, it printed out 4 copies each.  Also took long time to finish.

Why strange?


satimis

---

### Post by PaulFr on 2007-08-13
Maybe you have many copies of each repository in the /etc/apt/sources.list - check the output of```
grep -v '^#' /etc/apt/sources.list | grep -v '^$' | sort
```and look for duplicates.

---

### Post by satimis on 2007-08-13
> **PaulFr said:**
> Maybe you have many copies of each repository in the /etc/apt/sources.list - check the output of```
grep -v '^#' /etc/apt/sources.list | grep -v '^$' | sort
```and look for duplicates.
$ grep -v '^#' /etc/apt/sources.list | grep -v '^$' | sort```

deb http://archive.canonical.com/ubuntu feisty-commercial main
deb http://debian.linux.org.tw/ubuntu/ feisty-backports main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ feisty main restricted
deb http://debian.linux.org.tw/ubuntu/ feisty multiverse
deb http://debian.linux.org.tw/ubuntu/ feisty-security main restricted
deb http://debian.linux.org.tw/ubuntu/ feisty-security multiverse
deb http://debian.linux.org.tw/ubuntu/ feisty-security universe
deb http://debian.linux.org.tw/ubuntu/ feisty universe
deb http://debian.linux.org.tw/ubuntu/ feisty-updates main restricted
deb http://debian.linux.org.tw/ubuntu/ feisty-updates universe multiverse
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
deb http://www.getautomatix.com/apt feisty main
deb-src http://debian.linux.org.tw/ubuntu/ feisty-backports main restricted universe multiverse #Added by software-properties
deb-src http://debian.linux.org.tw/ubuntu/ feisty restricted main multiverse universe #Added by software-properties
deb-src http://debian.linux.org.tw/ubuntu/ feisty-security restricted main multiverse universe #Added by software-properties
deb-src http://debian.linux.org.tw/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties

```
Seems no duplication.  Would "feisty-security multiverse" and "feisty-security universe" be the same?


satimis

---

### Post by bsmith1051 on 2007-09-09
wow... I'm totally confused.  I've got an Epson 4990 and the default SANE driver doesn't support any of the advanced features (but otherwise works fine).  It sounds like installing the Epson 'iscan' is a real PITA -- is it worth it?  

The user guide shows that it has a simpler maybe-better-organized interface but didn't mention any of the advanced features.

---

