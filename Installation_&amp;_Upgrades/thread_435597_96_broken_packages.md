---
title: "96 broken packages"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by 16777216 on 2007-05-07
I have been getting this error for about three days and every method of fixing broken packages does not work.

I even deleted all cached package files  then redownloaded  it and i still get this error. 

dpkg: parse error, in file `/var/lib/dpkg/status' near line 7592 package `libgnomeui-0':
 field name `Priority*' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

### Post by Mongoose on 2007-05-07
That file is uber important for a debian system, and it seems to have been corrupted.  Open it  up read only in a text editor and paste the 10 lines before and 10 lines after the one given -- including the one given of course.  Me or one of the other old debian people can help you out.  I used to edit status by hand all the time back in the elder years.  Oh how I hate corrupt files.    You prob just need to fix a single line.  ;)

---

### Post by 16777216 on 2007-05-07
highlighting of source code, auto indentation and printing and print preview
 support.
 .
 gedit is also extensible through its plugin systmm, which currently
 includes support for spell checking, comparing files, viewing CVS
 ChangeLogs, and adjusting indentation levels.
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

Package: libgnomeui-0
Statu{: install ok inòtalled
Priority* optional
Section: libs
Installed-Size: 848
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: libgnomeui
Version: 2.07.92-0ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui²-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.14), libfontconfig1 (>= 2.4.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-° (>= 2.11.1), libgnomevfs2-0 (>, 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0), libjpeg62, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.15.6), libpopt0 (>= 1.10), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2®6.27), libxrandr2 (>= 2:1.2.0), libxrender1, libgnomeui-common (>= 2.17), libgnomeui-common (<< 2.18)
Suggests: gnome-icon-theme
Description: The GNOME 2 libraries (User Interface) - runtime files
 This packáge contains the shared library for the base GNOME library
 functions (User Inteòface functions).
Original-Maintainer: OndÅ&#153;ej S|rÃœ <ondrej@debéan.org>

P

---

### Post by Nythain on 2007-05-07
ok, im not an old debian veteran, but based on your error i would say modify the line
Priority* optional
to read
Priority*: optional

you're gonna have to open the file again with gksudo to be able to save the changes of course... and back the file up before making the change, but that should fix it

---

### Post by Mongoose on 2007-05-07
Yeah, Nythain is right it should look like:

Status: install ok installed
Priority: optional

You have some kind of locale issue?

---

### Post by 16777216 on 2007-05-07
Just tried that and I get a  bad package name in the "Depends" line. ( 7599 )
No, I should not have locale issues as I am in America and use english.
Note the odd chacters in the  package names, they look like OCR errors :confused: not like the errors you would see from just a corrupt file or a misstype.

Any way I replaced all of the superscript numbers and the ® and I still get the same error. 

dpkg: parse error, in file `/var/lib/dpkg/status' near line 7599 package `libgnomeui-0':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:


That worked!! Thank you for the help.


I found a status-old file and did a diff

/var/lib/dpkg# diff status status-old
7574c7574
<  gedit is a text editor which suppords most standard editor features,
---
>  gedit is a text editor which supports most standard editor features,
7581c7581
<  U&#65533;F-8 encoding in edited files. Its core feature set includes syntax
---
>  UTF-8 encoding in edited files. Its core feature set includes syntax
7585c7585
<  gedit is also extensible through its plugin systmm, which currently
---
>  gedit is also extensible through its plugin system, which currently
7598,7599c7598,7599
< Version: 2.07.92-0ubuntu1
< Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.14),&#65533;libfontconfig1 (>= 2.4.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomevfs2-0 (>, 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0), libjpeg62, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.15.6), libpopt0 (>= 1.10), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, libgnomeui-common (>= 2.17), libgnomeui-common (<< 2.18)
---
> Version: 2.17.92-0ubuntu1
> Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.14), libfontconfig1 (>= 2.4.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0), libjpeg62, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.15.6), libpopt0 (>= 1.10), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, libgnomeui-common (>= 2.17), libgnomeui-common (<< 2.18)
7602,7604c7602,7604
<  This pack&#65533;ge contains the shared library for the base GNOME library
<  functions (User Inte&#65533;face functions).
< Original-Maintainer: Ondrej <ondrej@debian.org>
---
>  This package contains the shared library for the base GNOME library
>  functions (User Interface functions).
> Original-Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
14302c14302
< Status: install ok installed
---
> Status: install ok unpacked
 
I will replace status with status-old and see how that goes as the old file seems to be correct.

It worked!! Thank you both for the help.

---

