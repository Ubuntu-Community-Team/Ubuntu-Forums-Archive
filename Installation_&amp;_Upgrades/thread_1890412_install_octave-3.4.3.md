---
title: "install octave-3.4.3"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by chaaa on 2011-12-03
I had some problems installing the newest version of octave first, but now everything is fine. In posting the steps that lead me to success, I hope I can save some people precious time they might want to use for doing mathematics.

(The Distribution I use is Kubuntu 10.04 LTS and I had octave 3.0.5 running)

0. download the octave-3.4.3 .tar.gz from [http://www.gnu.org/software/octave/download.html](http://www.gnu.org/software/octave/download.html) and unpack into a folder.
 
 1 . if not on your system yet, install the following package:
 
```
$ sudo apt-get install build-essential
``` This package contains an informational list of packages which are considered essential for building Debian packages. This package also depends on the packages on that list, to make it easy to have the build-essential packages installed. It includes the gcc/g++ compilers and libraries and  other utilities.

 2. ```
$ sudo  apt-get build-dep octave3.2
``` The dependencies of 3.4 are similar to those of 3.2., so this should get you the needed dependencies for 3.4. To make sure take a look at the list of dependencies for build from source [http://wiki.octave.org/wiki.pl?action=browse&diff=1&id=BuildFromSource](http://wiki.octave.org/wiki.pl?action=browse&diff=1&id=BuildFromSource) and install any further needed packages.
 
 3. I had the package fort77 installed which caused problems when I tried to build octave. Just dump the package.
 
4. The next two steps are crucial and solved my initial problems in building octave-3.4.3:
 
rename gfortran in /usr/bin:    
 
```
$ sudo mv /usr/bin/gfortran    /usr/bin/gfortran.ORG
```create a symbolic link:
 
     ```
$ sudo ln -s /usr/bin/gfortran-x.x   /usr/bin/gfortran
```(at x.x insert your version number for gfortran; in my case it was gfortran-4.4)
 
 5. Tell octave to build in gcc-x.x:
 
```
$ export CC=/usr/bin/gcc-x.x
``````
$ export CXX=/usr/bin/g++-x.x
``` 6. The rest is as usual:
 
cd into the folder with the downloaded octave-files and configure files:
 
```
$ ./configure
``````
$ make
```if you want you can now run octave in place to test before installing: 

     ```
$ ./run-octave
```hopefully octave works :) You can now run the package's built in tests. This step is also optional, but it might be good to make sure the programs that have been built behave as they should, before you decide to install them:
 
```
$ make check
```now, after everything has been built and tested, install octave (the default target is /usr/local):
 
     ```
$ sudo make install
```As a last step, to save disk space, you can remove files that ```
make
``` created and were needed just during the build process:
 
```
$ make clean
```(You should keep your makefile. It is useful if you want to uninstall octave by doing a simple make uninstall.)
 
7. If you want to install further packages or newer versions of packages (for example the package audio-1.1.4 with sound.m, soundsc.m etc. which are not contained in the normal installation), get them from [http://octave.sourceforge.net](http://octave.sourceforge.net) and install them in  /usr/local/share/octave/3.4.3/m where all your packages with .m-files should be.
 
8. Have fun with your free, open and powerful new toy!!

---

### Post by martin.k on 2011-12-19
Did you also have any luck with --enable-64 ?

3.2.x built easily with --enable-64, but 3.4.3 links against different libraries (e.g. BLAS and LAPACK), which are by default not 64bit in Ubuntu 10.04 :(

I am trying to work thru [http://www.gnu.org/software/octave/doc/interpreter/Compiling-Octave-with-64_002dbit-Indexing.html](http://www.gnu.org/software/octave/doc/interpreter/Compiling-Octave-with-64_002dbit-Indexing.html) right now, but progress is slow...

---

