---
title: "Error during installation: &quot;/bin/sh: 4: hd_install: not found&quot;"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by aleksandar.rachkov on 2013-11-17
Hi,

I am installing this software called HEASoft I need to analyze data with. And I thought that it'd be a great idea to build the source code distribution, instead of using the pre-compiled binary distribution. I am following the instruction given from the website: [http://heasarc.gsfc.nasa.gov/lheasoft/install.html](http://heasarc.gsfc.nasa.gov/lheasoft/install.html). And everything went fine until I did "make install" and in "install.log", I get the following error:

> make install
make[2]: Entering directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make hd-std-install
make[3]: Entering directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make[4]: Entering directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make hd-std-install-tasks
make[5]: Entering directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
/bin/sh: 4: hd_install: not found
make[5]: *** [hd-std-install-tasks] Error 127
make[5]: Leaving directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make[4]: *** [install-tasks] Error 2
make[4]: Leaving directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make[3]: *** [hd-std-install] Error 2
make[3]: Leaving directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/alex/Documents/heasoft-6.14/heacore/BUILD_DIR'
make[1]: *** [heacore] Error 2
make[1]: Leaving directory `/home/alex/Documents/heasoft-6.14/BUILD_DIR'
make: *** [install] Error 2

With my limited understanding, I think it says there is no hd_install file. But when I go in BUILD_DIR, there is indeed a "hd_install.c" file.
I looked up for similar problems, and some people were saying that maybe bin/sh is corrupted, but I don't see how that would be possible.

If anyone could help, I'd appreciate it greatly!

Thanks in advance.

---

### Post by steeldriver on 2013-11-17
There should be an **executable **hd_install file that was compiled **from **the hd_install.c file during the 'make' phase - did you run a separate 'make' before the 'make install'? if so were there any errors?

---

### Post by aleksandar.rachkov on 2013-11-17
> **steeldriver said:**
> There should be an **executable **hd_install file that was compiled **from **the hd_install.c file during the 'make' phase - did you run a separate 'make' before the 'make install'? if so were there any errors?

Thank you.
Yes, there was another make before that. It had the following error:

> xtloop.c:9:27: fatal error: X11/Intrinsic.h: No such file or directory
compilation terminated.
make[8]: *** [xtloop.o] Error 1
make[8]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/xpa'
make[7]: *** [subdir-xpa] Error 2
make[7]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[6]: *** [build-xpa] Error 2
make[6]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[5]: *** [hd-std-all-subdirs] Error 2
make[5]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[4]: *** [all-subdirs] Error 2
make[4]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[3]: *** [hd-std-all] Error 2
make[3]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/alex/Documents/heasoft-6.14/tcltk/BUILD_DIR'
make[1]: *** [tcltk] Error 2
make[1]: Leaving directory `/home/alex/Documents/heasoft-6.14/BUILD_DIR'
make: *** [all] Error 2

---

### Post by steeldriver on 2013-11-17
Did you install the X11 prerequisite(s) as indicated in the HEASOFT-INSTALL.TXT instructions? i.e.

```
sudo apt-get install xorg-dev
```

Did you pass any parameters on the configure commandline? or just plain ./configure ?

---

### Post by aleksandar.rachkov on 2013-11-17
OH wow, thank you so much!
I thought that when they wanted X11, all they need was libx11-dev, which I alread had.

Thank you so much!

---

