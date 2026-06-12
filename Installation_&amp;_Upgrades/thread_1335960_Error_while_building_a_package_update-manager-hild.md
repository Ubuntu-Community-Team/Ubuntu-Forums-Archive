---
title: "Error while building a package update-manager-hildon."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by prasanthp on 2009-11-24
While building a package update-manager-hildon, i got the following error..



boss:~/update-manager-hildon/update-manager-0.111.9# dpkg-buildpackage -rfakeroot -us -uc -sa

dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: 
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package update-manager
dpkg-buildpackage: source version 1:0.111.midboss1
dpkg-buildpackage: source changed by Prasanth P <prasanthp@cdac.in>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
python setup.py clean --all
running clean
'build/lib.linux-i686-2.5' does not exist -- can't clean it
'build/bdist.linux-i686' does not exist -- can't clean it
'build/scripts-2.5' does not exist -- can't clean it
find . -name "*.so" -exec rm {} \;
find . -name "*.o" -exec rm {} \;
find . -name "*.pyc" -exec rm {} \;
rm -f build-stamp
dh_clean
 dpkg-source -b update-manager-0.111.9
dpkg-source: info: using source format `1.0'
dpkg-source: warning: source directory 'update-manager-0.111.9' is not <sourcepackage>-<upstreamversion> 'update-manager-0.111.midboss1'
dpkg-source: info: building update-manager in update-manager_0.111.midboss1.tar.gz
dpkg-source: info: building update-manager in update-manager_0.111.midboss1.dsc
 debian/rules build
make: Nothing to be done for `build'.
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean
dh_installdirs
set -e; \
    for v in 2.4 2.5; do \
      python$v setup.py install --root=/root/update-manager-hildon/update-manager-0.111.9/debian/tmp/ --install-layout=deb   ; \
    done
usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help

error: option --install-layout not recognized
make: *** [install] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2


I got this link while trying to sort out the problem. 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=516586](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=516586)

But i couldn't find out a solution. Can any body help me.

I am using Debian based operating system.

---

### Post by prasanthp on 2009-11-26
I still couldn't find out the solution. Can any body plz help. :)

---

