---
title: "Install rpm file problem"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by philmetz on 2008-09-29
So i first try to convert the rpm file to deb by doing the following but this gives me an error as shown below:
```

philip@philip-laptop:~/Desktop$ sudo alien -k s_x86_64.rpm
Warning: Skipping conversion of scripts in package dell-nvidia: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Updated to build 100-14-19. Added support for Quadro FX1600M, FX360M
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/dell-nvidia
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libm.so.6 needed by debian/dell-nvidia/usr/bin/nvidia-xconfig (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Updated to build 100-14-19. Added support for Quadro FX1600M, FX360M
dpkg-gencontrol: error: current host architecture 'i386' does not appear in package's architecture list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: dell-nvidia-14.19: No such file or directory

```

What can i do?

---

### Post by oldos2er on 2008-09-29
What exactly are you trying to do? If you're trying to install video drivers, use System, Administration, Hardware Drivers. See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by philmetz on 2008-09-30
What about ATI graphics cards?

---

### Post by philmetz on 2008-09-30
how do you do that

---

### Post by oldos2er on 2008-09-30
> **philmetz said:**
> What about ATI graphics cards?

 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

 It helps if you state up front your hardware and what you're trying to do.

---

### Post by oldos2er on 2008-09-30
> **silve said:**
> what about the old fashioned way to install video card drivers?

 Care to be more specific?

---

### Post by tehbillick on 2008-10-01
Hello all,

I'm not sure what the original poster was trying to do, but I am having the same issue.  I am trying to install a cad program called lignumcad, which is only available as source and .rpm.  I suppose I could download the source and compile this, but the process shown here looks like a long struggle:

[http://lignumcad.sourceforge.net/doc/en/HTML/index.html](http://lignumcad.sourceforge.net/doc/en/HTML/index.html)

Anyhow, when I try to convert the package with alien, I get the same behavior.  I have been trying to find a way around the problem, but I can't find any resolutions specific to Hardy.  Thanks in advance for steering me in the right direction!


dr-teeth:~/lignumcad$ sudo alien -kdi lignumCAD-0.2-3.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Updated to 0.2 of lignumCAD. Moved installation to /opt.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/lignumcad
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx-envy from: /usr/lib32/libGL.so.1
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx-envy to: /usr/lib32/fglrx/libGL.so.1.xlibmesa
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx-envy from: /usr/lib32/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx-envy to: /usr/lib32/fglrx/libGL.so.1.2.xlibmesa
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Updated to 0.2 of lignumCAD. Moved installation to /opt.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: lignumCAD-0.2: No such file or directory
dr-teeth:~/lignumcad$

---

