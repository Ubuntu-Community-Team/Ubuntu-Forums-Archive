---
title: "Problem installing tgrep"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by ghantauke on 2011-03-08
I'm trying to install tgrep using the INSTALL file but I'm gettin errors. The following messages speaks for itself.

```

denish@ubuntu:~/tgrep$ ./INSTALL
 
****************************************************************
          THIS IS THE CONFIGURATION SCRIPT FOR TGREP
 
       Please answer all questions with full pathnames
****************************************************************
 
I cannot determine the gcc include path on your system.
  Please enter the gcc include path if it is available: /usr/include
 
/usr/src/linux/include was not found on your system.
  Please enter a substitute include path if it is available: /usr/src/linux-headers-2.6.35-24-generic
 
/usr/X11R6/include was not found on your system.
  Please enter a substitute include path if it is available: 
 
/usr/X11R6/lib was not found on your system.
  Please enter a substitute include path if it is available: 
 
Warning: /Xm was not found.  The X progress display will
not be available.
 
 
****************************************************************
The perl command is   :: /usr/bin/perl
The bison command is  :: /usr/bin/bison
The flex command is   :: /usr/bin/flex
The imake command is  :: /usr/bin/imake
gcc include path is   :: /usr/include
linux include path is :: /usr/src/linux-headers-2.6.35-24-generic
standard include path :: /usr/include
standard library path :: /usr/lib
 
Are these parameters correct? [y/n/q] y
continuing with configuration
 
Enter the directory where you wish to install the tgrep executables: 
  [the default is /home/denish/tgrep/bin : return = default] 
  :  
 
Enter the directory where you wish to install the tgrep corpora: 
  [the default is /home/denish/tgrep/data : return = default] 
  : 
 
The tgrep man pages are for the first section of the manual.
  Enter the directory where you wish to install
  the tgrep man pages (i.e. /usr/local/man/man1): 
  [the default is /home/denish/tgrep/doc/man1 : return = default ]
  : 
 
****************************************************************
install executables in      :: /home/denish/tgrep/bin
install corpora in        :: /home/denish/tgrep/data
install man pages in        :: /home/denish/tgrep/doc/man1
 
Are these parameters correct? [y/n/q] y
continuing with configuration
***** MAKING MAKEFILE IN DIRECTORY src/tools
***** MAKING MAKEFILE IN DIRECTORY src/environ
***** MAKING MAKEFILE IN DIRECTORY src/tgrep
***** MAKING MAKEFILE IN DIRECTORY bin
***** MAKING MAKEFILE IN DIRECTORY doc
***** MAKING MAKEFILE IN DIRECTORY data
***** MAKING MAKEFILE IN DIRECTORY /home/denish/tgrep/config
 
 
 
*********************************************************
 
THE CONFIGURATION STAGE OF THE BUILD PROCESS IS COMPLETE
 
If you experience trouble beyond this point you don't
need to run INSTALL again, you can just run 'make'
to make everything or 'make install' to make everything
and install everything. 
If need be, you should run make from the directory /home/denish/tgrep
 
*********************************************************
 
 
 
***** MAKING AND INSTALLING FROM DIRECTORY src/tools
make[1]: Entering directory `/home/denish/tgrep/src/tools'
gcc -c -o ArgPack.o ArgPack.c -g -I/usr/include -I/usr/src/1-headers-2.6.35-24-generic -I -I/usr/include -I. -Dconst= -DMEMDEBUG=0   -Wall -m486 -O4 
cdenish@ubuntu:~/tgrep$ ./INSTALL
 
****************************************************************
          THIS IS THE CONFIGURATION SCRIPT FOR TGREP
 
       Please answer all questions with full pathnames
****************************************************************
 
I cannot determine the gcc include path on your system.
  Please enter the gcc include path if it is available: /usr/include
 
/usr/src/linux/include was not found on your system.
  Please enter a substitute include path if it is available: /usr/src/linux-headers-2.6.35-24-generic
 
/usr/X11R6/include was not found on your system.
  Please enter a substitute include path if it is available: 
 
/usr/X11R6/lib was not found on your system.
  Please enter a substitute include path if it is available: 
 
Warning: /Xm was not found.  The X progress display will
not be available.
 
 
****************************************************************
The perl command is   :: /usr/bin/perl
The bison command is  :: /usr/bin/bison
The flex command is   :: /usr/bin/flex
The imake command is  :: /usr/bin/imake
gcc include path is   :: /usr/include
linux include path is :: /usr/src/linux-headers-2.6.35-24-generic
standard include path :: /usr/include
standard library path :: /usr/lib
 
Are these parameters correct? [y/n/q] y
continuing with configuration
 
Enter the directory where you wish to install the tgrep executables: 
  [the default is /home/denish/tgrep/bin : return = default] 
  :  
 
Enter the directory where you wish to install the tgrep corpora: 
  [the default is /home/denish/tgrep/data : return = default] 
  : 
 
The tgrep man pages are for the first section of the manual.
  Enter the directory where you wish to install
  the tgrep man pages (i.e. /usr/local/man/man1): 
  [the default is /home/denish/tgrep/doc/man1 : return = default ]
  : 
 
****************************************************************
install executables in      :: /home/denish/tgrep/bin
install corpora in        :: /home/denish/tgrep/data
install man pages in        :: /home/denish/tgrep/doc/man1
 
Are these parameters correct? [y/n/q] y
continuing with configuration
***** MAKING MAKEFILE IN DIRECTORY src/tools
***** MAKING MAKEFILE IN DIRECTORY src/environ
***** MAKING MAKEFILE IN DIRECTORY src/tgrep
***** MAKING MAKEFILE IN DIRECTORY bin
***** MAKING MAKEFILE IN DIRECTORY doc
***** MAKING MAKEFILE IN DIRECTORY data
***** MAKING MAKEFILE IN DIRECTORY /home/denish/tgrep/config
 
 
 
*********************************************************
 
THE CONFIGURATION STAGE OF THE BUILD PROCESS IS COMPLETE
 
If you experience trouble beyond this point you don't
need to run INSTALL again, you can just run 'make'
to make everything or 'make install' to make everything
and install everything. 
If need be, you should run make from the directory /home/denish/tgrep
 
*********************************************************
 
 
 
***** MAKING AND INSTALLING FROM DIRECTORY src/tools
make[1]: Entering directory `/home/denish/tgrep/src/tools'
gcc -c -o ArgPack.o ArgPack.c -g -I/usr/include -I/usr/src/1-headers-2.6.35-24-generic -I -I/usr/include -I. -Dconst= -DMEMDEBUG=0   -Wall -m486 -O4 
cc1: error: unrecognized command line option "-m486"
make[1]: *** [ArgPack.o] Error 1
make[1]: Leaving directory `/home/denish/tgrep/src/tools'
exit: 1: Illegal number: -1
make: *** [install] Error 2
 
************************************************************
 It seems that the build process did not go smoothly
 If you cannot diagnos and fix the problem yourself
 send email to tgrep-support@linc.cis.upenn.edu
 containing a copy of all the output from this failed
 installation process.
************************************************************
c1: error: unrecognized command line option "-m486"
make[1]: *** [ArgPack.o] Error 1
make[1]: Leaving directory `/home/denish/tgrep/src/tools'
exit: 1: Illegal number: -1
make: *** [install] Error 2
 
************************************************************
 It seems that the build process did not go smoothly
 If you cannot diagnos and fix the problem yourself
 send email to tgrep-support@linc.cis.upenn.edu
 containing a copy of all the output from this failed
 installation process.
************************************************************


```I downloaded the tgrep package from [ftp://ftp.crl.ucsd.edu/pub/tgrep/tgrep.tar.gz](ftp://ftp.crl.ucsd.edu/pub/tgrep/tgrep.tar.gz) and I'm using ubuntu.

---

