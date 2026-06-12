---
title: "VNC2SWF, anyone able to install this?"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by nehalem on 2005-05-23
I can't install this.  It gives me this on the make:

gcc  -DHAVE_LIBZ=1 -DHAVE_LIBMING=1  -I. -DVNC_SOCKLEN_T=socklen_t  -I/usr/X11R6/include  -O2 -Wall  -g -c argsresources.c
argsresources.c:26:28: X11/Xaw/Toggle.h: No such file or directory
argsresources.c: In function `SetFullScreenState':
argsresources.c:460: error: `XtNstate' undeclared (first use in this function)
argsresources.c:460: error: (Each undeclared identifier is reported only once
argsresources.c:460: error: for each function it appears in.)
argsresources.c: In function `SetBGR233State':
argsresources.c:464: error: `XtNstate' undeclared (first use in this function)
argsresources.c: In function `SetAutoState':
argsresources.c:468: error: `XtNstate' undeclared (first use in this function)
make: *** [argsresources.o] Error 1


Has anyone had success installing this?  I could really use this for some stuff I'm working on.

---

### Post by xy77 on 2005-06-06
get libming ~2003 from
[http://bozu.sytes.net/~tyuyu/diary/?200402c#200402231](http://bozu.sytes.net/~tyuyu/diary/?200402c#200402231)
and get vnc2swf_0.3-1_i386.deb from
[http://ftp.arege.jp/debian-arege/dists/sid/vnc2swf/binary-i386/?C=S;O=D](http://ftp.arege.jp/debian-arege/dists/sid/vnc2swf/binary-i386/?C=S;O=D)
and dpkg -i them. (I got this one from somewhere else, but can't remember; if this doesn't work, tell me and I'll put up the .debs on my homepage)

And make sure to read
[http://www.unixuser.org/~euske/vnc2swf/vnc2swf.html#dist](http://www.unixuser.org/~euske/vnc2swf/vnc2swf.html#dist)
before complaining about fragmented movies.

Hope it works for you.
- David (xy77)

EDIT: I created a live-CD with vnc2swf support for my company (no Linux-boxes here apart from the webserver), and noticed, libfontconfig1 (>2.3 IIRC) is necessary if you want to use swftools. It's not in the regular repository, I got it from [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffontconfig%2Flibfontconfig1_2.3.1-2_i386.deb&md5sum=cd328d7f8bd869f526a880054b577009&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffontconfig%2Flibfontconfig1_2.3.1-2_i386.deb&md5sum=cd328d7f8bd869f526a880054b577009&arch=i386&type=main)

---

