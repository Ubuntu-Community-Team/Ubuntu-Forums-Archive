---
title: "checkinstall fails to create Debian package"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-02-24
When I try to 'checkinstall' TCL8.5a3 I get the following:
```
tom@wraith:~/src/tcl/tcl8.5a3/unix$ sudo checkinstall --install=no --pakdir=../..

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

The checkinstallrc file was not found at:
/usr/local/lib/checkinstall/checkinstallrc

Assuming default values.

The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: n

Please choose the packaging method you want to use.
Slackware [S], RPM [R] or Debian [D]? D


Please write a description for the package.
End your description with an empty line or EOF.
>> TCL8.5a3
>>

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "unix" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

*** Warning: The package version "" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values:

0 -  Maintainer: [ root@wraith ]
1 -  Summary: [ TCL8.5a3 ]
2 -  Name:    [ unix ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ unix ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Installing libtcl8.5.so to /usr/lib/
Installing tclsh as /usr/bin/tclsh8.5
Installing tclConfig.sh to /usr/lib/
Installing libtclstub8.5.a to /usr/lib/
Installing time zone data
    Creating tzdata
        Creating US
        Creating Etc
        Creating Asia
        Creating Arctic
        Creating Canada
        Creating Brazil
        Creating America
            Creating Indiana
            Creating Kentucky
            Creating Argentina
            Creating North_Dakota
        Creating Europe
        Creating Pacific
        Creating Chile
        Creating Indian
        Creating Mexico
        Creating Antarctica
        Creating Australia
        Creating Atlantic
        Creating SystemV
        Creating Africa
Installing message catalogs
    Creating msgs
Making directory /usr/lib/tcl8.5/opt0.4
Making directory /usr/lib/tcl8.5/http1.0
Making directory /usr/lib/tcl8.5/encoding
Making directory /usr/lib/tcl8.5/../tcl8
Making directory /usr/lib/tcl8.5/../tcl8/8.2
Making directory /usr/lib/tcl8.5/../tcl8/8.3
Making directory /usr/lib/tcl8.5/../tcl8/8.5
Installing header files
Installing library files to /usr/lib/tcl8.5
Installing library http1.0 directory
Installing package http 2.5.1 as a Tcl Module
Installing library opt0.4 directory
Installing package msgcat 1.4.1 as a Tcl Module
Installing package tcltest 2.2.8 as a Tcl Module
Installing library encoding directory
Making directory /usr/man
Making directory /usr/man/man1
Making directory /usr/man/man3
Making directory /usr/man/mann
Installing and cross-linking top-level (.1) docs
Installing and cross-linking C API (.3) docs
Installing and cross-linking command (.n) docs

======================== Installation successful ==========================

Copying files to the temporary directory...OK

Striping ELF binaries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y

Erasing temporary files...OK

Deleting doc-pak directory...OK

Deleting temp dir...OK

```
bellow is the error log:
```
dpkg-deb: parse error, in file `/var/tmp/laRFnAWbNrZEYMGpPoUK/package/DEBIAN/control' near line 10 package `unix':
 empty value for version

```

its the same with TK8.5a3
ps. This happens to my on 2computer.

---

### Post by frodon on 2006-02-24
> *** Warning: The package name "unix" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

*** Warning: The package version "" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values:

0 -  Maintainer: [ root@wraith ]
1 -  Summary: [ TCL8.5a3 ]
2 -  Name:    [ unix ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ unix ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:At this step checkinstall is telling you that there isn't a version number for this package and therefore the .deb creation will surely fail, so instead of press enter to continue press "3" at this step and put a version number and then follow the checkinstall process as usual and it should work without any problems.

---

### Post by andrewsawyer on 2006-02-24
Which version of Ubuntu are you running?  I know there is a problem with checkinstall in Dapper.  You might try compiling it yourself directly from their site.  That's what I had to do.  I still get problems making debs for certain progs, and I'm not quite sure why, but most seem to work.

---

### Post by ashrack on 2006-02-24
[QUOTE=andrewsawyer]Which version of Ubuntu are you running?  I know there is a problem with checkinstall in Dapper.  You might try compiling it yourself directly from their site.  That's what I had to do.  I still get problems making debs for certain progs, and I'm not quite sure why, but most seem to work.[/QUOTE]
running checkinstall160 which I DL and installed from their website

---

### Post by ashrack on 2006-02-24
FRODON
tanx, that fixed the problem.

Now am cursious, what is this
```
The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: 
```

---

