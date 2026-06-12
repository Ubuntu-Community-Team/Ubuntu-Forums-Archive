---
title: "Configure warnings installing XOOPIC from Berkeley Plasma Physics Group"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by rogersjg on 2013-04-22
I downloaded and unpacked the sources, Then I established the dependancies with Linux sudo command according to the following README.INSTALL.
```
XOOPIC source is available via www at [http://langmuir.eecs.berkeley.edu/pub/codes](http://langmuir.eecs.berkeley.edu/pub/codes)

Most if this file is old, but here is the quickstart. Read on if you have trouble.
: This is a standard ./configure, make, make install system.
: start with the script 'run_conf.sh' - it is a nicer way to pass arguments to configure
        and it is the same for xoopic and xgrafix (you need to install xgrafix first)
: once you have edited run_conf.sh to fit your needs, use it to configure xgrafix, then install it:
    $> sh run_conf.sh
    $> make && sudo make install # note only sudo if you need root privileges to write the destination
: then once that completes, use _the same_ run_conf.sh to configure xoopic:
    $> sh run_conf.sh
    $> make && cp xg/xoopic /path/to/where/I/want/xoopic

That should do it!

bash_completion generally has nice tab completion for introspection of available options to configure
($>./configure<tab><tab> will show your options)

############################
# Dependencies:
############################
building and running xgrafix/xoopic depend on the following headers/libraries/programs:
    X11, Xpm, Tcl/Tk, gcc, imagemagick, bison
    
optional xoopic dependencies:
    Fortran
    MPI for parallel runs
    HDF5 for parallel or high performance dump files
    libpng for png diagnostics
    fftw
    fftw3


dependencies can be installed on Ubuntu (or likely any Debian based distro) with the command:
sudo aptitude install gcc g++ gfortran build-essential automake \
    tk-dev imagemagick bison libx11-dev libxpm-dev libpng-dev \
    fftw-dev  libfftw3-dev h5utils hdf5-tools libhdf5-serial-*\

the first two lines are necessary, the last installs optional fftw/hdf5 dependencies

On Fedora, these dependencies can be installed with:
sudo yum install gcc gcc-gfortran gcc-c++ automake libX11-devel libXpm-devel \
        ImageMagick bison tk-devel libpng-devel \
        hdf5 hdf5-devel

On SUSE, install the following packages with your package manager:
        gcc gcc-c++ gcc-fortran automake xorg-x11-devel make
        tk-devel bison libpng-devel imagemagick hdf5 hdf5-devel


##################
# Configure / build/ install
##################
For a new install:

edit the run_conf.sh file to match your system.  For a basic install, the only
thing you are likely to edit is `prefix` - the install location.

then you can do:
sh run_conf.sh # configure the build

make # build the program
# or, if you have a multiprocessor machine, this can go faster with:
make -j 4 #(that's 4 threads, you can do as many or as few as you want)

# If you are building xgrafix, do:
make install # sudo make install if you need root privileges to write to $prefix/{bin|lib|include}

test the xgrafix build with: 
./ctest/xtest # from the xgrafix root dir.

Once you have built and installed xgrafix, you can build xoopic. run_conf.sh is the same for
both xoopic and xgrafix, so if you configured run_conf.sh in xgrafix, use the same one in xoopic.

The process to build xoopic is the same as xgrafix, except skip the 'make install' step, since you only
need the binary file in 'xg/xoopic'. You can test xoopic with:
./xoopic -i input/ebeam1a.inp # from the xoopic root dir

once xoopic is done, you can install it with:
cp xoopic $prefix/bin/

note that you do not need to do 'make install' for xoopic, just place the binary './xoopic' anywhere in your path

where prefix is defined as in:
prefix=/usr/local # to install for all users
or
prefix=$HOME # to install just for you (assuming ~/bin is already in your path)

**************************************
The rest of this file is pretty old...    

XOOPIC has been compiled successfully on the following UNIX systems running
X11R5 or better:

OS        Machine     compiler    library
-------------------------------------------------------------------------
HP-UX A.09.05    HP 712/80    g++2.7.2    libg++2.7.1
DEC UNIX 3.2    DEC 200/4/233    g++2.7.2    libg++2.7.1
DEC UNIX 3.2    DEC 200/4/233    CXX5.1        vendor supplied
                using DEC CXX 5.1 is not recommended for XOOPIC
DEC UNIX 4.0C    PWS 600AU    g++2.8.0    libg++2.8.0
DEC UNIX 4.0C    PWS 600AU    egcs-1.0.1    egcs libraries
DEC UNIX 4.0C    PWS 600AU    CXX6.0        vendor supplied.
DEC UNIX 4.0D    PWS 600AU    CXX6.0        vendor supplied.
DEC UNIX 4.0D    DEC 8400    CXX6.0        vendor supplied.
SunOS 4.1.x    Sparc 2        g++2.7.2    libg++2.7.1
Solaris 2.5    UltraSPARC    g++2.7.2    
Solaris 2.6    UltraSPARC    Sun CC 4.2    vendor supplied
AIX 3.2        IBM 590        g++2.7.2    libg++2.7.1
AIX 3.2        IBM 590        xlC 1.00 --  had to modify the code,
                    and turn off optimization on some
                    files.  Furthermore, the compiled
                    code was 1/2 as fast as g++.
Solaris 2.4    Sparc 10    Sun c++4.0.1    
                (required a few simple changes)

Linux        PPro        g++2.7.2, g++2.8.0
Linux/Alpha    21164        g++2.7.2, g++2.8.0
FreeBSD        K6        g++2.7.2
-- Most of this is outdated, but 2009 versions have been compiled on the following:
both 32/64 bit:
    Ubuntu Linux 8.10 - 9.10, gcc 4.2-4.4, tcl/tk 8.4-8.5
    Mac OSX 10.4.8,10.5.7,10.6.1 - using MacPorts or Fink for tcl/tk
    Fedora Core 8 (64) - gcc4.1
    Fedora Core 11 (32) - gcc4.4 
    openSUSE 11 (32) - gcc4.3

****************************************************************************
If possible ENLIST THE AID OF YOUR SYSTEM ADMINISTRATOR FOR COMPILING XOOPIC.

WARNING:  g++ 2.6.1, g++ 2.6.2, and g++ 2.6.3 are BROKEN and WILL NOT 
compile XOOPIC (on most systems).  I don't know about previous versions.

ALSO: g++2.7.2 on Windows NT 4.0 does NOT work.
****************************************************************************




The rest of this file is possibly outdated:
**********
To compile and install XOOPIC, you need the following public domain
software packages which we do not maintain:


* g++            (/pub/GNU/gcc-2.7.2.tar.gz at gatekeeper.dec.com)
* libg++        (/pub/GNU/libg++-2.7.?.tar.gz at gatekeeper.dec.com)

OR DEC CXX instead of g++ and libg++

* libtcl7.4.a (or later)    
* libtk4.0.a  (or later)        
* libXpm.a        
* libXGrafix2.50 (or later)   ([http://ptsg.eecs.berkeley.edu](http://ptsg.eecs.berkeley.edu))

*************************************************
*** NOTE: Requirement for the XGrafix version ***
*************************************************
Update on Aug. 16, 2005 by H.C. KIM

 To make this version of xoopic work properly, the recent version
of XGrafix (later than Mar. 29, 2005) needs to be installed.
 Otherwise, you may see "core dumped" when restoring from a dump file.
*************************************************

Once you have a c++ compiler, libtcl.a libtk.a libXpm.a, you are ready to
begin:

0)  Get the sources:  
    [http://ptsg.eecs.berkeley.edu](http://ptsg.eecs.berkeley.edu)

    You may already have these and can omit this step.

1)  Unpack the sources:
    >tar -xvzf xoopic.tar.gz

     You should get a directory named oopic with these files:
    README Makefile physics/ advisor/ xg/ xgrafix/ input/ g++-fixes/ doc/
    configure
    physics/ contains the basic physical models for XOOPIC
    advisor/ contains the input file reader and input sanity checking
    xgrafix/ contains the graphics library used by XOOPIC
    input/ contains sample input files for XOOPIC
    g++-fixes/ contains any fixes you may need to make to g++ to get
           it to work
    doc/ contains documentation.
    bench/ benchmarks of XOOPIC
    + other misc. files..

2)  Compile and install XGrafix.
    (XGrafix has its own instructions)
    
3)  Run ./configure

     Once you have a c++ compiler, libXGC250.a, libXpm.a, libtcl*.a, libtk*.a,
     you are ready to start compiling xoopic.  

     To begin, run "configure", which will try to find all the libraries
     and headers needed, and which will accept parameters indicating
     configuration options or library locations.

     In the directory where you have: 
    README Makefile physics/ advisor/ xg/ xgrafix/ input/
     
     ./configure

     Pay attention to the messages configure gives.  If it fails to 
     automatically find something such as libXpm.a, it will prompt
     you to tell it where to find that file.

     configure --help 
     will give you a list of configure options.

     As an example, this command will cause XOOPIC to use the compiler
     'cxx' instead of the default 'g++':

     ./configure --with-CXX=cxx

     If HDF5 library is not installed in your systems,
     you need to give an option of '--disable-hdf5':

     ./configure --disable-hdf5

     Depending on how idiosyncratic your system installation is, you
     might have to give a very complex configure comand such as:

     ./configure --with-CXX=cxx --with-tclsh=/home/tcl/bin 
    --x-includes=/usr/X11/include --x-libraries=/sww/X11/lib
    --with-xpm=/usr/local/Xpm/lib --with-XGRAFIX-lib=/usr/local/tmp

     However, that should only be necessary if your system administrator
     likes to install things in non-standard locations.

     Configure, when successful, should convert Makefile.in in each of
     . advisor/ physics/ and xg/ and convert them to a Makefile.

4)   Run make

     make

     This should go into each of physics/ advisor/, and xg/,
     and create the binary xg/xoopic for you.

     If the compile fails, complaining of missing include files
     or libraries, try editing */Makefile to add the appropriate
     includes or libraries.

     If the link fails with missing symbols, it is likely that 
     the version of tcl/tk that XOOPIC is trying to use is a
     mismatch to the XGrafix library.  XGrafix must be configured
     to use either version 7.4/4.0 of the tcl/tk libraries,
     or configured to use version 7.5/4.1 or higher.  If 
     XGrafix was configured for the wrong tcl/tk libraries,
     then XOOPIC won't link!

     Possible problems:  the compile fails, giving errors involving
     cstring.h.  This is a g++2.7.0 problem.  
     A fix for this is in g++-fixes.

    b) upon starting XOOPIC, xgrafix reports that it can't find 
    a tcl/tk initialization file.

    Solution:  Figure out where the file xgrafix is looking for is,
    and fix xgrafix to find it.  These are some in particular:
    init.tcl     in the tcl lib directory, (usually /usr/local/lib/tcl)
    init.tk     in the tk lib directory, (usually /usr/local/lib/tk)
    xgsetup.tcl    in your xgrafix directory

    If the problem is with finding init.tcl, and init.tk, then probably
    these libraries are misinstalled.  If xgsetup.tcl is not found,
    you probably didn't set XGTCL correctly when building xgrafix.
    Double check this and recompile if necessary.

To run,

     xoopic -i input/dring.inp

    or whatever input file is appropriate for you.




Bugs:  email bugreports to [EMAIL="xoopic@langmuir.eecs.berkeley.edu"]xoopic@langmuir.eecs.berkeley.edu[/EMAIL]
```

 Executing xgrafix/run_conf.sh gives the following warning messages:
```
precisiont3400@ubuntu:~/Fusion/XOOPIC/Downloads/xgrafix$ ./run_conf.sh#2
bash: ./run_conf.sh#2: Permission denied
precisiont3400@ubuntu:~/Fusion/XOOPIC/Downloads/xgrafix$ ./run_conf.sh#2
configuring with options: --prefix=/usr/local --with-SCALAR=double --enable-fulloptimize --with-XGRAFIX-lib=/usr/local/lib --with-XGRAFIX-include=/usr/local/include 
configure: WARNING: unrecognized options: --with-XGRAFIX-lib, --with-XGRAFIX-include
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
Using C++ compiler g++
Using C compiler gcc
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking whether time.h and sys/time.h may both be included... yes
checking for BSD-compatible nm... 
install-sh/usr/bin/nm -B
Setting the flags per system and C++ compiler: g++
checking for g++... /usr/bin/g++
Serial C++ compiler is `g++'
checking g++ version... g++
configure: WARNING: Caution: version  is not known to work.
configure: WARNING: C++ compiler may generate code for this processor only.
checking for -fsquangle... no
checking how to build libraries... with ar cr  
checking for gcc... /usr/bin/gcc
Serial C compiler is `gcc'
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether c++ compiler supports exception handling... yes
checking whether c++ compiler supports typename... yes
checking whether c++ compiler can explicitly instantiate templates... yes
checking whether c++ compiler supports RTTI... yes
checking whether c++ compiler supports namespaces... yes
checking whether c++ compiler has complex in the namespace std... yes
checking whether c++ compiler has streams in the namespace std... yes
checking whether c++ compiler can overload const type conversions... yes
checking whether c++ compiler knows mutable... yes
checking whether template friends need brackets... yes
checking whether nontype template operators are allowed... no
checking whether static variables can be declared generally... yes
configure: WARNING: Fortran libraries will be invalid.
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for ranlib... ranlib
checking what the library suffix is... .a
checking how to install libraries... with ${INSTALL} -m 644
configure: WARNING: x11.m4 is obsolete.  Please use AC_PATH_X or AC_PATH_XTRA.
checking for X11/Xlib.h... /usr/include/X11/Xlib.h
checking for libX11.a... no
checking for libX11.so... no
configure: error: Unable to find libX11.a or libX11.so in /usr/lib32:/usr/X11R6/lib:/usr/lib:/usr/local/lib:/lib:/usr/X11/lib:/usr/openwin/lib:/usr/dt/lib:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.  Set the appropriate directory using --with-X11_LIBDIR
precisiont3400@ubuntu:~/Fusion/XOOPIC/Downloads/xgrafix$ 
```

The problem seems to be the path name of libX11.a etc. How do I find the pathname? Or how do I avoid the final "configure: error:..." message?
Any advice would be greatly appreciated.
Dr. Joel Rogers, plasma physicist

---

### Post by dino99 on 2013-04-22
Look the 2 first output lines: "permission denied" .So you need to make that package executable first:

sudo chmod +x xgrafix  (use the exact name : case sensitive)

---

### Post by rogersjg on 2013-04-22
I already fixed that in the 3rd line. Making a file executable is easily done without Linux via the Permissions option of the file manager.
Thanks anyway.

---

### Post by rogersjg on 2013-04-24
Those configure problems have gone away. It was a $PATH error in finding the needed header files.
For now I don't need help.

---

### Post by ahripon on 2013-04-24
If you looking any information?
please visit your website, [http://informationfor.com/](http://informationfor.com/)

Information For General Information, Travel,  Awards, Important Day, Missing People, New Farce, News, Report, Business, Financial, Entertainment, Celebrity, Comics, Fashion, Movie, Music, Television, Lifestyle, Culture, Health, Love, Technology, Freelance, Software, Web Design, Telecom, Automobile, Electronic, Science, Religion,The Sport, Cricket, football, tennis, golf and many more information.

---

### Post by siddharth.krishnam on 2013-12-04
Hello, I'm facing the same problem. I have xgrafix and x11 installed but I'm getting libX11.a and libX11.so missing. Could you please tell me how you solved this problem? 

Thank you,

Siddharth

---

