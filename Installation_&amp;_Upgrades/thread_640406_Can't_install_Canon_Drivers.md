---
title: "Can't install Canon Drivers"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Ilias83 on 2007-12-14
I need help to install Canon PIXMA iP4300 drivers.
Unfortunatelly Canon provides only .rpm files to install drivers.
Her is what I get trying to convert to .rpm file to .deb:

ilias@ilias-desktop:~/Documents/Programs$ sudo alien ~/Documents/Programs/cnijfilter-ip4300-2.70-2.i386.rpm
Warning: Skipping conversion of scripts in package cnijfilter-ip4300: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cnijfilter-ip4300
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcmcm294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcnclbjcmd294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcmcm294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpess294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcnclui294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcmcm294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcmcm294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpess294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcnclapi294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcnclbjcmd294.so' not recognized
dpkg-shlibdeps: warning: format of 'NEEDED libcnbpcnclui294.so' not recognized
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libxml.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml (soname 1, path libxml.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libxml.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml (soname 1, path libxml.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libtiff.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libtiff (soname 3, path libtiff.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpng.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpng (soname 3, path libpng.so.3, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cnijfilter-ip4300-2.70: No such file or directory
ilias@ilias-desktop:~/Documents/Programs$ 

After that all i get is a folder named cnijfilter-ip4300-2.70.

Please help.
What can I do?

---

### Post by Partyboi2 on 2007-12-17
I would say what is probably happening is alien is trying to convert the 32 bit rpm into a 64 bit deb, which it can't do.
the 32 bit rpm needs to be converted to a 32 bit deb
I did alittle digging around and come across this site
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4300](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4300)
Looks like they have the 64 bit rpm that you can convert.

---

