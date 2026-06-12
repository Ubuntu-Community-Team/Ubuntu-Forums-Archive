---
title: "QtWorkbench installation"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Black_Moon on 2009-12-26
Code::Blocks & QT.

installed C::B
> 
sudo apt-get install codeblocks
All works but without QT UI support (UI made by QtDesigner).

Tryed to add QtWorkbench plugin to C::B using [http://code.google.com/p/qtworkbench/wiki/PluginInstallation](http://code.google.com/p/qtworkbench/wiki/PluginInstallation)

> 
1.    svn checkout svn://svn.berlios.de/codeblocks/trunk codeblocks
2. cd codeblocks/
3. wget [http://qtworkbench.googlecode.com/files/QtWorkbench-src-0.5.1.tar.gz](http://qtworkbench.googlecode.com/files/QtWorkbench-src-0.5.1.tar.gz)
4. tar zxf QtWorkbench-src-0.5.1.tar.gz
5. patch --unified --strip=0 --forward --input=qtworkbench.patch
6. ./bootstrap
7. ./configure --prefix=/opt/codeblocks-svn --with-contrib-plugins=qtworkbench
8.  make
9.  sudo make install
10. /opt/codeblocks-svn/bin/codeblocks
on p 5 errors apper> romeo@Romeo:~/codeblocks$ patch --unified --strip=0 --forward --input=qtworkbench.patch
patching file configure.in
Hunk #1 FAILED at 341.
1 out of 1 hunk FAILED -- saving rejects to file configure.in.rej
patching file src/plugins/contrib/Makefile.am
Hunk #1 FAILED at 54.
Hunk #2 FAILED at 71.
Hunk #3 FAILED at 88.
3 out of 3 hunks FAILED -- saving rejects to file src/plugins/contrib/Makefile.am.rej
patching file acinclude.m4
Hunk #1 FAILED at 220.
Hunk #2 FAILED at 238.
Hunk #3 FAILED at 253.
Hunk #4 succeeded at 216 with fuzz 2 (offset -89 lines).
Hunk #5 FAILED at 242.
4 out of 5 hunks FAILED -- saving rejects to file acinclude.m4.rej
> 
romeo@Romeo:~/codeblocks$ ./bootstrap
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.in:7: installing `./config.guess'
configure.in:7: installing `./config.sub'
configure.in:9: installing `./install-sh'
configure.in:9: installing `./missing'
src/base/tinyxml/Makefile.am: installing `./depcomp'
> 
romeo@Romeo:~/codeblocks$ make
make: *** &#1053;&#1077; &#1079;&#1072;&#1076;&#1072;&#1085;&#1099; &#1094;&#1077;&#1083;&#1080; &#1080; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; make-&#1092;&#1072;&#1081;&#1083;.  &#1054;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;.
romeo@Romeo:~/codeblocks$ sudo make install
make: *** &#1053;&#1077;&#1090; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; &#1076;&#1083;&#1103; &#1089;&#1073;&#1086;&#1088;&#1082;&#1080; &#1094;&#1077;&#1083;&#1080; `install'.  &#1054;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;.
romeo@Romeo:~/codeblocks$ /opt/codeblocks-svn/bin/codeblocks
bash: /opt/codeblocks-svn/bin/codeblocks: No such file or directory

Where's mistake? How C::B works with QtWorkBench, Qt UI (made in QtDesigner)?
Thanks.

---

### Post by gsmanners on 2009-12-26
According to the qtworkbench page, they stopped at CB v8.02. I don't think the patch will work with the svn unless someone forks qtworkbench.

[http://code.google.com/p/qtworkbench/](http://code.google.com/p/qtworkbench/)
[http://www.codeblocks.org/downloads/source](http://www.codeblocks.org/downloads/source)

---

### Post by Black_Moon on 2009-12-27
> **gsmanners said:**
> According to the qtworkbench page, they stopped at CB v8.02. 

It's not good.
So, C::B will not work with Qt UI (designed in QtDesigner)?
May be there's some another plugin for QT in C::B?

:confused:

---

### Post by gsmanners on 2009-12-27
What does the svn version have that you need? Can't you just use the source from C::B 8.02 (which I give you a link to)?

---

### Post by Black_Moon on 2009-12-29
> **gsmanners said:**
>  Can't you just use the source from C::B 8.02 (which I give you a link to)?

Downloaded C::B tar archieve (_codeblocks-8.02-src.tar.bz2_) from Berlios source (_[http://download.berlios.de/codeblocks/codeblocks-8.02-src.tar.bz2](http://download.berlios.de/codeblocks/codeblocks-8.02-src.tar.bz2)_)

Skipped step 1 - 
_svn checkout svn://svn.berlios.de/codeblocks/trunk codeblocks_

step 5
> romeo@Romeo:~/codeblocks$ patch --unified --strip=0 --forward --input=qtworkbench.patch
patching file configure.in
Hunk #1 succeeded at 363 (offset 22 lines).
patching file src/plugins/contrib/Makefile.am
Hunk #1 FAILED at 54.
Hunk #2 FAILED at 71.
Hunk #3 succeeded at 106 with fuzz 2 (offset 18 lines).
2 out of 3 hunks FAILED -- saving rejects to file src/plugins/contrib/Makefile.am.rej
patching file acinclude.m4
Hunk #1 succeeded at 234 with fuzz 2 (offset 14 lines).
Hunk #2 succeeded at 255 with fuzz 2 (offset 17 lines).
Hunk #3 succeeded at 271 with fuzz 2 (offset 18 lines).
Hunk #4 succeeded at 383 with fuzz 2 (offset 78 lines).
Hunk #5 succeeded at 412 with fuzz 2 (offset 81 lines).
> romeo@Romeo:~/codeblocks$ ./bootstrap
svn: '.' is not a working copy
svn: '.' is not a working copy
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
romeo@Romeo:~/codeblocks$ > 
make
sudo make install
build & install, some mistakes found...


And get /opt/codeblocks-svn directory, includes /lib, /share & /src. (no /bin directoryy in /opt/codeblocks-svn).

And what else?:confused:

---

### Post by gsmanners on 2009-12-29
Looks like patch for the makefile doesn't work. A developer could make it work by fixing the patch, but I doubt that's going to happen at this point.

---

### Post by Black_Moon on 2009-12-29
Looks that qtworkbench wouldn't work with C::B..:( 

Forced to use KDeveloper or QDeveloper


**gsmanners,** thanks for your cooperation.

---

### Post by jiapei100 on 2010-01-01
Hi, same situation here.

Ubuntu 9.10 + CodeBlocks 8.02 + qtworkbench 0.60 alpha

won't work at all.

So sad...

Refer to my post at 
[http://forums.codeblocks.org/index.php/topic,11776.0.html]("http://forums.codeblocks.org/index.php/topic,11776.0.html")

---

