---
title: "Installing Marratech from RPM"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by BramWillemsen on 2010-01-11
Hi everyone,

A course i am enrolled in uses Marratech to record the lectures. The problem is that the linux client is distributed as a .rpm package. When i try to convert it to a .deb package i get some errors unfortunately. I really need this software to work in order to study for the test. I tried running it in the newest version of wine, but the program frantically refreshes the screen making it impossible to see anything of the program.
When i try to build a .deb package from .rpm with the command "sudo alien -d Marratech-6.1.i586.rpm" i get this mess. A lot of dependency problems and an architecture problem amd64 vs i386. Should i just give up on this program in linux and install dual boot?

```

error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/marratech
dh_compress
dh_makeshlibs
objdump: debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libJdbcOdbc.so.gz: File format not recognized
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libmanagement.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libmanagement.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libzip.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libzip.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libjaas_unix.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libjaas_unix.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libnio.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libnet.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libnio.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjmutil.so needed by debian/marratech/usr/local/marratech/Marratech6.1/lib/libjmh261.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjawt.so needed by debian/marratech/usr/local/marratech/Marratech6.1/lib/libjmfjawt.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/marratech/usr/local/marratech/Marratech6.1/jre/lib/i386/libverify.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: error: couldn't find library libstdc++.so.5 needed by debian/marratech/usr/local/marratech/Marratech6.1/lib/libmVideo.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `Marratech-6.1': No such file or directory

```

---

### Post by davec64 on 2010-01-11
Hi, I'm not familiar with Maratech but I found this:

[http://help.nceas.ucsb.edu/Installing_Marratech_on_Linux]("http://help.nceas.ucsb.edu/Installing_Marratech_on_Linux")

It mentions installing 32-bit compatibility libraries if running on the AMD64 build of Ubuntu.

Once you've got them on this might affect the dependancies. :)

---

### Post by BramWillemsen on 2010-01-11
Thanks for your suggestion. I tried installing it that way, no errors are generated. I followed all the steps. When i launch the program it just does not work. The progress bar is stuck halfway and nothing happens for minutes. No CPU activity either :( see the picture that i attached



edit: i decided to just install windows XP in virtualbox. It was quite easy to set up and marratech works fine there.

---

### Post by davec64 on 2010-01-11
Sorry I couldn't have been more help!

The omly thing I would have suggested was running Marratech from the terminal, that way you get any error messages displayed there.

Virtualbox is always a great back-up :)

---

