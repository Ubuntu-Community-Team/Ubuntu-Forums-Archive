---
title: "epson scanner install help"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by mikeprosceo on 2011-01-09
I am trying to load the linux driver for an epson 3170 scanner on to my ubuntu 10.10 64 bit laptop. I downloaded the rpm package (iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-9400-1.10.0-1.c2.i386.rpm) to my desktop. I extracted the files and  and tried to use alien to convert the rpm to a deb file in terminal.  The following are the steps I took and the message I received.  Before I tried this I installed libsane-dev. and libsane-extras.  
michael@michael-laptop:~/Desktop$ sudo alien -d iscan-2.10.0-1.c2.i386.rpm 
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm 
Warning: Use the --scripts parameter to include the scripts. 
mkdir: cannot create directory `iscan-2.10.0': File exists 
unable to mkdir iscan-2.10.0:  at /usr/share/perl5/Alien/Package.pm line 257. 
   I also tried using sudo alien -k iscan.2.10.0-1.c2.i386.rpm and got a file not found message.  I am totally lost and have no idea what to try.  Can anyone help?  Thanks - Mike

---

### Post by reidi on 2011-02-01
Did you ever get your 3170 working?  I have not been able to with Meerkat 64-bit.  As far as installing the iscan rpm's, here is how I did it (sorry, I lost the link.  Also, substitute your iscan version for "dbvis..." below):

When using alien to convert this .rpm to .deb like so ...

Code:
 sudo alien --veryverbose -c -d dbvis_linux_7_0_4.rpm
it stops with the follwing error : 

Code:
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
        find dbvis-7.0.4 -type d -exec chmod 755 {} ;
find: `dbvis-7.0.4': No such file or directory
        rm -rf dbvis-7.0.4
So apparently the architecture of the package is set wrongly, or alien is not detecting it correctly, who cares? Well I do. So, let us stop the conversion half way with the -g option like so ( if you executed the previous command, please first remove the build directory via "sudo rm -fr dbvis-7.0.4" ):

Code:
sudo alien --veryverbose -c -d -g dbvis_linux_7_0_4.amd64.rpm
to quote from the alien man page :

Code:
-g, --generate
           Generate a temporary directory suitable for building a package
           from, but do not actually create the package. This is useful if you
           want to move files around in the package before building it. The
           package can be built from this temporary directory by running
           "debian/rules binary", if you were creating a Debian package, or by
           running "rpmbuild -bb <packagename>.spec" if you were creating a
           Red Hat package.
So now we can make changes and the build the binary .deb by changing to the build directory that alien created, in this case dbvis-7.0.4, and executing the command :

Code:
sudo ./debian/rules binary
but not just yet. First we need to change the architecture to amd64. So change to the ./dbvis-7.0.4/debian/ directory and edit the control file, it should have contents similar to this (and is named control):

Code:
Source: dbvis
Section: alien
Priority: extra
Maintainer: blah von bliep <blah@bliep.com>

Package: dbvis
Architecture: i386
Depends: ${shlibs:Depends}
Description: 
 DbVisualizer
 .
 (Converted from a rpm package by alien version 8.78.)
change the i386 item to amd64 and save, using your favorite editor.

now change one directory back like so :
Code:
cd ..
you should be in the build directory, in this case dbvis-7.0.4, and now to start the .deb build, run the rules file like so :
Code:
sudo ./debian/rules binary
Lots of magic behind the scenes code will run giving output similar to this :

Code:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/dbvis
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `dbvis' in `../dbvis_7.0.4-2_amd64.deb'.
and you will end with a dbvis_7.0.4-2_amd64.deb package.

Now use dpkg to install this package like so :

Code:
sudo dpkg --install dbvis_7.0.4-2_amd64.deb

---

### Post by mikeprosceo on 2012-04-16
No,I never did get it to work.  I gave up.  I thought it might be easier with 11.10 but not so.  I thought there was a force-architecture command to convert 32 bit packages to work in 64 bit.  I will read over what you sent and try it.  Thanks

---

