---
title: "Howto install dbvisualizer on Ubuntu 9.10 amd64"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by meddle on 2010-03-03
or How I Learned to Stop Worrying and Love the Alien.

One of the download options for dbvisualizer is a .rpm package ( [http://www.dbvis.com/products/dbvis/download/](http://www.dbvis.com/products/dbvis/download/) )

This package has no architecture and contains a java application.

When using alien to convert this .rpm to .deb like so ...

```
 sudo alien --veryverbose -c -d dbvis_linux_7_0_4.rpm
```

it stops with the follwing error : 

```
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
        find dbvis-7.0.4 -type d -exec chmod 755 {} ;
find: `dbvis-7.0.4': No such file or directory
        rm -rf dbvis-7.0.4
```

So apparently the architecture of the package is set wrongly, or alien is not detecting it correctly, who cares? Well I do. So, let us stop the conversion half way with the -g option like so ( if you executed the previous command, please first remove the build directory via "sudo rm -fr dbvis-7.0.4" ):

```
sudo alien --veryverbose -c -d -g dbvis_linux_7_0_4.amd64.rpm
```

to quote from the alien man page :

```
-g, --generate
           Generate a temporary directory suitable for building a package
           from, but do not actually create the package. This is useful if you
           want to move files around in the package before building it. The
           package can be built from this temporary directory by running
           "debian/rules binary", if you were creating a Debian package, or by
           running "rpmbuild -bb <packagename>.spec" if you were creating a
           Red Hat package.
```

So now we can make changes and the build the binary .deb by changing to the build directory that alien created, in this case dbvis-7.0.4, and executing the command :

```
sudo ./debian/rules binary
```

but not just yet. First we need to change the architecture to amd64. So change to the ./dbvis-7.0.4/debian/ directory and edit the control file, it should have contents similar to this (and is named control):

```
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
```
change the i386 item to amd64 and save, using your favorite editor.

now change one directory back like so :
```
cd ..
```
you should be in the build directory, in this case dbvis-7.0.4, and now to start the .deb build, run the rules file like so :
```
sudo ./debian/rules binary
```
Lots of magic behind the scenes code will run giving output similar to this :

```
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
```

and you will end with a dbvis_7.0.4-2_amd64.deb package.

Now use dpkg to install this package like so :

 ```
sudo dpkg --install dbvis_7.0.4-2_amd64.deb
```

and run dbvisualizer like so :

```
dbvis
```

I have sun-java packages installed, so I cannot comment on the default java install.

References:
[1] [http://women.debian.org/wiki/English/BuildingWithoutHelper](http://women.debian.org/wiki/English/BuildingWithoutHelper)
[2] alien man page

---

### Post by dontmatta on 2010-04-22
It worked like a charm, thanks!  This is one of the best GUI based DB managers out there.

---

### Post by Minister on 2010-10-14
Thank you, this is an excellent post for us 64 bit people, installed DbVisualizer 7.1.3 Linux x86 (RPM archive) the 52 MB download with no problems, using alien to convert from rpm to deb package and the rest of the recipe from this post.:)

---

### Post by gurpal2000 on 2010-11-03
This doesn't seem to work with verson 7.1.3 on Ubuntu 10.04 ?

dpkg-gencontrol: error: syntax error in debian/control at line 11: continued value line not in field
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/dbvis.substvars -Pdebian/dbvis returned exit code 9
make: *** [binary-arch] Error 9

---

### Post by rogerw05465 on 2011-02-08
... and I got similar errors on DBvis 7.1.4 on Ubuntu 10.10. I was not altering the control file, as I am on 32 bit, but otherwise following the thread as written.  Any thoughts on what is happening?

Roger

[FONT=monospace]rogerw@rogerw-acer:~/Desktop/tempDBvis/dbvis-7.1.4$ sudo ./debian/rules binary
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/dbvis
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: syntax error in debian/control at line 11: continued value line not in field
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/dbvis.substvars -Pdebian/dbvis returned exit code 9
make: *** [binary-arch] Error 9
rogerw@rogerw-acer:~/Desktop/tempDBvis/dbvis-7.1.4$ sudo ./debian/rules binary
[/FONT]

---

### Post by rhowe on 2011-06-13
It looks like alien is generating a duff control file.

Remove the blank line below "Description: DbVisualizer"

Also, instead of "Architecture: amd64" or "Architecture: i386", it should probably be "Architecture: all". It's a Java application and a cursory glance didn't turn up any architecture-specific files in there.

---

### Post by deathsheep7 on 2011-12-02
Thank you for documenting these instructions.

I just wanted to confirm I successfully installed dbviz 8.0.6 on my debian testing (32 bit).

as rhowe had suggested, I edited my debian/control file to use the keyword "all", and deleted the extra newline in the description (not sure if it mattered).

<rant>
Additionally, I also had to install sun-java6-jdk to actually run dbviz (surprise, surprise) which is slightly non-trivial on debian now.
</rant>

---

### Post by Kride81 on 2012-03-09
Tried this with Ubuntu 11.10 and DBVisualizer 8.0.8
When running
```
sudo dpkg --install dbvis_8.0.8-2_amd64.deb
```
I get this kind of error. (Tried also with 'all')

[FONT="Lucida Console"]Relocation is broken in this rpm release.
If you specified a relocation, please reinstall the package
with the default settings.[/FONT]

Any way to get over this?

---

### Post by pcampa on 2012-04-15
@Kride81
I had the same error on my Oneiric.
There must be some error in the conversion to .deb.
Just download and run the installer instead:
[http://www.dbvis.com/products/dbvis/download/]("http://www.dbvis.com/products/dbvis/download/")

---

### Post by mpopet on 2012-11-12
> **Kride81 said:**
> Tried this with Ubuntu 11.10 and DBVisualizer 8.0.8
When running
```
sudo dpkg --install dbvis_8.0.8-2_amd64.deb
```I get this kind of error. (Tried also with 'all')

[FONT=Lucida Console]Relocation is broken in this rpm release.
If you specified a relocation, please reinstall the package
with the default settings.[/FONT]

Any way to get over this?


What I did to fix the package:
 -edit the <DBVIS_FOLDER>/debian/postinst and prerm file:
   replace all occurences of  RPM_INSTALL_PREFIX0 with RPM_INSTALL_PREFIX

and then rebuild the .deb again:
sudo ./debian/rules binary

---

