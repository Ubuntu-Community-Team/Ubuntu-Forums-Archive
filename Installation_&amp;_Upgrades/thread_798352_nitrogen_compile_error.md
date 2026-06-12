---
title: "nitrogen compile error"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by jipke on 2008-05-18
I've got Openbox up and running & trying to compile nitrogen from source to set a wallpaper.

As mentioned on urukrama's blog ([http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/), very good guide BTW) I've installed build-essential, checkinstall and the depencies libgtkmm-2.4-dev libgtk2.0-dev.

However, this is the output I get:

```
wout@laptop:~/_dump/nitrogen-1.3$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@laptop ]
1 -  Summary: [ graphicall app to set a desktop wallpaper ]
2 -  Name:    [ nitrogen ]
3 -  Version: [ 1.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ nitrogen-1.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in po
make[1]: Entering directory `/home/wout/_dump/nitrogen-1.3/po'
/bin/mkdir -p /usr/local/share
if test "nitrogen" = "gettext-tools"; then \
	  /bin/mkdir -p /usr/local/share/gettext/po; \
	  for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	  for file in Makevars; do \
	    rm -f /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/wout/_dump/nitrogen-1.3/po'
Making install in src
make[1]: Entering directory `/home/wout/_dump/nitrogen-1.3/src'
make[2]: Entering directory `/home/wout/_dump/nitrogen-1.3/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'nitrogen' '/usr/local/bin/nitrogen'
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './nitrogen.1' '/usr/local/share/man/man1/nitrogen.1'
make[2]: Leaving directory `/home/wout/_dump/nitrogen-1.3/src'
make[1]: Leaving directory `/home/wout/_dump/nitrogen-1.3/src'
Making install in data
make[1]: Entering directory `/home/wout/_dump/nitrogen-1.3/data'
Making install in icons
make[2]: Entering directory `/home/wout/_dump/nitrogen-1.3/data/icons'
make[3]: Entering directory `/home/wout/_dump/nitrogen-1.3/data/icons'
make[3]: Nothing to be done for `install-exec-am'.
../../data/icon-theme-installer -t "hicolor" -s "." -d "x" -b "/usr/local/share/icons/hicolor" -m "/bin/bash /home/wout/_dump/nitrogen-1.3/install-sh -d" -x "/usr/bin/install -c -m 644" -i apps,nitrogen-128.png apps,nitrogen-16.png apps,nitrogen-22.png apps,nitrogen-32.png apps,nitrogen-48.png devices,video-display-16.png actions,wallpaper-bestfit-16.png actions,wallpaper-centered-16.png actions,wallpaper-scaled-16.png actions,wallpaper-tiled-16.png mimetypes,image-x-generic-16.png
Installing 128x128 nitrogen.png into hicolor icon theme
chmod: changing permissions of `/usr/local/share/icons/hicolor/128x128/apps': No such file or directory
Failed to create directory /usr/local/share/icons/hicolor/128x128/apps
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/wout/_dump/nitrogen-1.3/data/icons'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/wout/_dump/nitrogen-1.3/data/icons'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/wout/_dump/nitrogen-1.3/data'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

Can you help me? I'm relativily new to this. Thanks in advance.

---

### Post by urukrama on 2008-05-18
It looks for the hicolor icons in /usr/*local*/share/hicolor and can't find them. By default they are in /usr/share/hicolor.

Try compiling and installing nitrogen with the following commands:

```
./configure --prefix='/usr'
make
sudo checkinstall
```

I just tried this out on Hardy and that works fine. The *./configure --prefix='/usr'* command ensure that the package will be installed in /usr/ and not /usr/local/.

Thanks for bringing this to my attention. I'll make the needed changes in the Openbox guide.

---

### Post by jipke on 2008-05-20
thanks, adding --prefix='/usr' to ./configure did the trick.

---

