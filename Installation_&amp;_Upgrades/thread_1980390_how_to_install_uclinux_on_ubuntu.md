---
title: "how to install uclinux on ubuntu"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by alexdb2012 on 2012-05-15
hi,


 Iam using ubuntu 10.04 ,now i want to install uclinux on my ubuntu.Please tel me the procedureeeeeeeee.




Thanks,
Alex

---

### Post by Kobalt on 2012-05-15
Here is how to start by installing the uClinux emulator : [http://www.ucdot.org/archive/tb/tb20020807.shtml](http://www.ucdot.org/archive/tb/tb20020807.shtml)

---

### Post by kc1di on 2012-05-15
See this page:

[http://www.ucdot.org/archive/tb/tb20020807.shtml]("http://www.ucdot.org/archive/tb/tb20020807.shtml")

---

### Post by alexdb2012 on 2012-05-15
sir,


Thanks, i followed that site, and i installed Xcopilot (uclinux first version).

[COLOR=#222222]    cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs login
  Just press enter at the password prompt,  and then run: 
      cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs checkout xcopilot
[/COLOR]
I used above commands to install in my terminal.


According to that site the output will be "Xcopilot is ready to use",but for me i got the following output.
alex-laptop:~$ cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs checkout xcopilot
cvs checkout: CVS password file /home/alex/.cvspass does not exist - creating a new file
cvs checkout: Updating xcopilot
U xcopilot/AUTHORS
U xcopilot/COPYING
U xcopilot/ChangeLog
U xcopilot/INSTALL
U xcopilot/Makefile.am
U xcopilot/Makefile.in
U xcopilot/NEWS
U xcopilot/README
U xcopilot/README.uClinux
U xcopilot/TODO
U xcopilot/acconfig.h
U xcopilot/aclocal.m4
U xcopilot/bittypes.h
U xcopilot/case.fancy.xpm
U xcopilot/case.xpm
U xcopilot/cmap_mgr.c
U xcopilot/cmap_mgr.h
U xcopilot/config.h.in
U xcopilot/configure
U xcopilot/configure.in
U xcopilot/display.c
U xcopilot/display.h
U xcopilot/fakecall.c
U xcopilot/fakecall.h
U xcopilot/icon.xpm
U xcopilot/icon2.xpm
U xcopilot/install-sh
U xcopilot/main.c
U xcopilot/main.h
U xcopilot/missing
U xcopilot/mkinstalldirs
U xcopilot/open_app.c
U xcopilot/open_app.h
U xcopilot/optutil.c
U xcopilot/optutil.h
U xcopilot/pdebug.c
U xcopilot/pdebug.h
U xcopilot/pilotcpu.c
U xcopilot/pilotcpu.h
U xcopilot/ser-tcp.c
U xcopilot/stamp-h.in
U xcopilot/xcopilot.1
U xcopilot/xcopilot.c
U xcopilot/xcopilot.sgml
cvs checkout: Updating xcopilot/debian
U xcopilot/debian/README.debian
U xcopilot/debian/changelog
U xcopilot/debian/control
U xcopilot/debian/copyright
U xcopilot/debian/menu
U xcopilot/debian/postinst
U xcopilot/debian/postrm
U xcopilot/debian/rules
U xcopilot/debian/substvars
cvs checkout: Updating xcopilot/gdb-stub
U xcopilot/gdb-stub/Makefile.am
U xcopilot/gdb-stub/Makefile.in
U xcopilot/gdb-stub/low-xcopilot.c
U xcopilot/gdb-stub/remote-utils.c
U xcopilot/gdb-stub/server.c
U xcopilot/gdb-stub/server.h
U xcopilot/gdb-stub/utils.c
cvs checkout: Updating xcopilot/mc68k
U xcopilot/mc68k/BUILD68K.C
U xcopilot/mc68k/GENCPU.C
U xcopilot/mc68k/Makefile.am
U xcopilot/mc68k/Makefile.in
U xcopilot/mc68k/TABLE68K
U xcopilot/mc68k/cpu0.c
U xcopilot/mc68k/cpu1.c
U xcopilot/mc68k/cpu2.c
U xcopilot/mc68k/cpu3.c
U xcopilot/mc68k/cpu4.c
U xcopilot/mc68k/cpu5.c
U xcopilot/mc68k/cpu6.c
U xcopilot/mc68k/cpu7.c
U xcopilot/mc68k/cpu8.c
U xcopilot/mc68k/cpu9.c
U xcopilot/mc68k/cpuA.c
U xcopilot/mc68k/cpuB.c
U xcopilot/mc68k/cpuC.c
U xcopilot/mc68k/cpuD.c
U xcopilot/mc68k/cpuE.c
U xcopilot/mc68k/cpuF.c
U xcopilot/mc68k/cputbl.c
U xcopilot/mc68k/cputbl.h
U xcopilot/mc68k/custom.c
U xcopilot/mc68k/custom.h
U xcopilot/mc68k/dragonball.h
U xcopilot/mc68k/fab_custom.c
U xcopilot/mc68k/memory.c
U xcopilot/mc68k/memory.h
U xcopilot/mc68k/newcpu.c
U xcopilot/mc68k/newcpu.h
U xcopilot/mc68k/shared.h
U xcopilot/mc68k/sysdeps.h
cvs checkout: Updating xcopilot/mx
U xcopilot/mx/Makefile.am
U xcopilot/mx/Makefile.in
U xcopilot/mx/alert.c
U xcopilot/mx/alert.h
U xcopilot/mx/basic.c
U xcopilot/mx/basic.h
U xcopilot/mx/buttons.c
U xcopilot/mx/buttons.h
U xcopilot/mx/filesel.c
U xcopilot/mx/filesel.h
U xcopilot/mx/libmx.h
U xcopilot/mx/menu.c
U xcopilot/mx/menu.h
U xcopilot/mx/request.c
U xcopilot/mx/request.h
U xcopilot/mx/select.c
U xcopilot/mx/select.h
U xcopilot/mx/test_filesel.c
U xcopilot/mx/test_menu.c

Is write?


Sir, myself is very new to this,please tel me  the step by step procedure.
I mean which directory at which place.Now i runed above command from my home direcory,i got confusion ,i have to execute ARM progams in uclinux.





Thanks in Advance.

---

### Post by alexdb2012 on 2012-05-15
sir,


Thanks, i followed that site, and i installed Xcopilot (uclinux first version).

[COLOR=#222222]    cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs login
  Just press enter at the password prompt,  and then run: 
      cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs checkout xcopilot
[/COLOR]
I used above commands to install in my terminal.


According to that site the output will be "Xcopilot is ready to use",but for me i got the following output.
Alex-laptop:~$ cvs -d:pserver:anonymous@cvs.uclinux.org:/var/cvs checkout xcopilot
cvs checkout: CVS password file /home/davipriya/.cvspass does not exist - creating a new file
cvs checkout: Updating xcopilot
U xcopilot/AUTHORS
U xcopilot/COPYING
U xcopilot/ChangeLog
U xcopilot/INSTALL
U xcopilot/Makefile.am
U xcopilot/Makefile.in
U xcopilot/NEWS
U xcopilot/README
U xcopilot/README.uClinux
U xcopilot/TODO
U xcopilot/acconfig.h
U xcopilot/aclocal.m4
U xcopilot/bittypes.h
U xcopilot/case.fancy.xpm
U xcopilot/case.xpm
U xcopilot/cmap_mgr.c
U xcopilot/cmap_mgr.h
U xcopilot/config.h.in
U xcopilot/configure
U xcopilot/configure.in
U xcopilot/display.c
U xcopilot/display.h
U xcopilot/fakecall.c
U xcopilot/fakecall.h
U xcopilot/icon.xpm
U xcopilot/icon2.xpm
U xcopilot/install-sh
U xcopilot/main.c
U xcopilot/main.h
U xcopilot/missing
U xcopilot/mkinstalldirs
U xcopilot/open_app.c
U xcopilot/open_app.h
U xcopilot/optutil.c
U xcopilot/optutil.h
U xcopilot/pdebug.c
U xcopilot/pdebug.h
U xcopilot/pilotcpu.c
U xcopilot/pilotcpu.h
U xcopilot/ser-tcp.c
U xcopilot/stamp-h.in
U xcopilot/xcopilot.1
U xcopilot/xcopilot.c
U xcopilot/xcopilot.sgml
cvs checkout: Updating xcopilot/debian
U xcopilot/debian/README.debian
U xcopilot/debian/changelog
U xcopilot/debian/control
U xcopilot/debian/copyright
U xcopilot/debian/menu
U xcopilot/debian/postinst
U xcopilot/debian/postrm
U xcopilot/debian/rules
U xcopilot/debian/substvars
cvs checkout: Updating xcopilot/gdb-stub
U xcopilot/gdb-stub/Makefile.am
U xcopilot/gdb-stub/Makefile.in
U xcopilot/gdb-stub/low-xcopilot.c
U xcopilot/gdb-stub/remote-utils.c
U xcopilot/gdb-stub/server.c
U xcopilot/gdb-stub/server.h
U xcopilot/gdb-stub/utils.c
cvs checkout: Updating xcopilot/mc68k
U xcopilot/mc68k/BUILD68K.C
U xcopilot/mc68k/GENCPU.C
U xcopilot/mc68k/Makefile.am
U xcopilot/mc68k/Makefile.in
U xcopilot/mc68k/TABLE68K
U xcopilot/mc68k/cpu0.c
U xcopilot/mc68k/cpu1.c
U xcopilot/mc68k/cpu2.c
U xcopilot/mc68k/cpu3.c
U xcopilot/mc68k/cpu4.c
U xcopilot/mc68k/cpu5.c
U xcopilot/mc68k/cpu6.c
U xcopilot/mc68k/cpu7.c
U xcopilot/mc68k/cpu8.c
U xcopilot/mc68k/cpu9.c
U xcopilot/mc68k/cpuA.c
U xcopilot/mc68k/cpuB.c
U xcopilot/mc68k/cpuC.c
U xcopilot/mc68k/cpuD.c
U xcopilot/mc68k/cpuE.c
U xcopilot/mc68k/cpuF.c
U xcopilot/mc68k/cputbl.c
U xcopilot/mc68k/cputbl.h
U xcopilot/mc68k/custom.c
U xcopilot/mc68k/custom.h
U xcopilot/mc68k/dragonball.h
U xcopilot/mc68k/fab_custom.c
U xcopilot/mc68k/memory.c
U xcopilot/mc68k/memory.h
U xcopilot/mc68k/newcpu.c
U xcopilot/mc68k/newcpu.h
U xcopilot/mc68k/shared.h
U xcopilot/mc68k/sysdeps.h
cvs checkout: Updating xcopilot/mx
U xcopilot/mx/Makefile.am
U xcopilot/mx/Makefile.in
U xcopilot/mx/alert.c
U xcopilot/mx/alert.h
U xcopilot/mx/basic.c
U xcopilot/mx/basic.h
U xcopilot/mx/buttons.c
U xcopilot/mx/buttons.h
U xcopilot/mx/filesel.c
U xcopilot/mx/filesel.h
U xcopilot/mx/libmx.h
U xcopilot/mx/menu.c
U xcopilot/mx/menu.h
U xcopilot/mx/request.c
U xcopilot/mx/request.h
U xcopilot/mx/select.c
U xcopilot/mx/select.h
U xcopilot/mx/test_filesel.c
U xcopilot/mx/test_menu.c

Is write?


Sir, myself is very new to this,please tel me  the step by step procedure.
I mean which directory at which place.Now i runed above command from my  home direcory,i got confusion ,i have to execute ARM progams in uclinux.





Thanks in Advance.

---

