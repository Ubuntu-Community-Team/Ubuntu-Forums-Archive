---
title: "Problems with checkinstall during installation of QwtPlot3D"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by Martin Aulbach on 2007-07-24
Hi,

I want to compile and install the QwtPlot3D library ( [http://qwtplot3d.sourceforge.net/](http://qwtplot3d.sourceforge.net/) ) on my Feisty system. This library is not available in the Ubuntu repositories. Therfore I downloaded the source code, untarred and compiled it. Instead of ./configure the Makefile of this program is made with qmake. Therefore I created the Makefile with the command

**qmake**

and then started compiling with

**make**

This succeeded and all the library files and other files have been created. However, if I want to make a deb package of this library with checkinstall,

**sudo checkinstall**

an error occurs during the execution of checkinstall:

```
cp: cannot stat `//var/tmp/iirHVKSRYrBRmojYHYNrM/newfiles.tmp': No such file or directory
```

The resulting dep package then only contains a few document files, whereas the important library files etc are missing. Below is the whole output of checkinstall:

```

martin@martin-dell:~/Downloads/qtiplot/qwtplot3d$ sudo checkinstall 
Password:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> QwtPlot3D
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@martin-dell ]
1 -  Summary: [ QwtPlot3D ]
2 -  Name:    [ qwtplot3d ]
3 -  Version: [ 20070724 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ qwtplot3d ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: Nothing to be done for `install'.

======================== Installation successful ==========================

Copying documentation directory...
./
./COPYING
./doc/
./doc/Doxyfile.doxygen
./doc/web/
./doc/web/navigation/
./doc/web/navigation/doxygen.png
./doc/web/navigation/menu.css
./doc/web/navigation/sflogo.png
./doc/web/navigation/doxygen.css
./doc/footer.html
cp: cannot stat `//var/tmp/iirHVKSRYrBRmojYHYNrM/newfiles.tmp': No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/martin/Downloads/qtiplot/qwtplot3d/qwtplot3d_20070724-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r qwtplot3d

**********************************************************************

```

Does anybody know why checkinstall can't include all the files into the deb and why the error message arises? /var/tmp has 777-permissions and a change of the temporary directory to ~/tmp yielded the same error message. Thanks for any help!

---

### Post by Martin Aulbach on 2007-07-25
*push* no one here who knows what to do?

---

