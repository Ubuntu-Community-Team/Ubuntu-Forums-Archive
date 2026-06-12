---
title: "compiling octave-3.6.4 on 12.04 and cannot complete configuration"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by pr0gramr7 on 2013-08-23
Hello all and thank you in advance for any suggestions, 

I have been trying to install gnu octave-3.6.4 on my system but am facing a little hang up. But I believe I am almost done.

my kernel info (uname -a):   Linux OBJECTIVE 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I have downloaded the following package and have been trying to build it. The following is the output of the command "aptitude show octave":
____________________________________________________________________________________________________________

Package: octave                          
State: not installed
Version: 3.6.4-1~ppa1~precise1
Priority: extra
Section: math
Maintainer: Debian Octave Group <pkg-octave-devel@lists.alioth.debian.org>
Architecture: amd64
Uncompressed Size: 4,909 k
Depends: libamd2.2.0 (>= 1:3.4.0), libarpack2 (>= 2.1), libblas3gf | libblas.so.3gf | libatlas3gf-base,
         libc6 (>= 2.14), libccolamd2.7.1 (>= 1:3.4.0), libcholmod1.7.1 (>= 1:3.4.0), libcolamd2.7.1 (>=
         1:3.4.0), libcurl3-gnutls (>= 7.16.2-1), libcxsparse2.2.3 (>= 1:3.4.0), libfftw3-3, libfltk1.1
         (>= 1.1.7), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglpk0 (>= 4.30),
         libgraphicsmagick++3, libgraphicsmagick3 (>= 1.3.5), liblapack3gf | liblapack.so.3gf |
         libatlas3gf-base, liboctave1 (= 3.6.4-1~ppa1~precise1), libqhull5 (>= 2003.1), libstdc++6 (>=
         4.6), texinfo, octave-common (= 3.6.4-1~ppa1~precise1)
Recommends: gnuplot-x11 | gnuplot-qt, libatlas3gf-base | libopenblas-base, pstoedit
Suggests: octave-info, octave-doc, octave-htmldoc
Conflicts: octave3.2, octave3.2, octave
Replaces: octave3.2, octave3.2
Provided by: octave3.2
Description: GNU Octave language for numerical computations
 Octave is a (mostly Matlab (R) compatible) high-level language, primarily intended for numerical
 computations. It provides a convenient command-line interface for solving linear and nonlinear problems
 numerically. 
 
 Octave can be dynamically extended with user-supplied C++ files.
_____________________________________________________________________________


At the end of the output for "./configure" is the following:

Octave is now configured for x86_64-unknown-linux-gnu

  Source directory:            .
  Installation prefix:         /usr/local
  C compiler:                  gcc   -Wall -W -Wshadow -Wformat -Wpointer-arith -Wmissing-prototypes -Wstrict-prototypes -Wwrite-strings -Wcast-align -Wcast-qual -g -O2      -pthread
  C++ compiler:                g++   -I/usr/local/include/freetype2 -I/usr/local/include   -I/usr/local/include    -Wall -W -Wshadow -Wold-style-cast -Wformat -Wpointer-arith -Wwrite-strings -Wcast-align -Wcast-qual -g -O2
  Fortran compiler:            gfortran -O
  Fortran libraries:            -L/usr/lib/gcc/x86_64-linux-gnu/4.6 -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../.. -lgfortran -lm -lquadmath
  Lex libraries:               
  LIBS:                        -lm  

  AMD CPPFLAGS:                
  AMD LDFLAGS:                 
  AMD libraries:               -lamd
  ARPACK CPPFLAGS:             
  ARPACK LDFLAGS:              
  ARPACK libraries:            
  BLAS libraries:              -lblas
  CAMD CPPFLAGS:               
  CAMD LDFLAGS:                
  CAMD libraries:              -lcamd
  CARBON libraries:            
  CCOLAMD CPPFLAGS:            
  CCOLAMD LDFLAGS:             
  CCOLAMD libraries:           -lccolamd
  CHOLMOD CPPFLAGS:            
  CHOLMOD LDFLAGS:             
  CHOLMOD libraries:           -lcholmod
  COLAMD CPPFLAGS:             
  COLAMD LDFLAGS:              
  COLAMD libraries:            -lcolamd
  CURL CPPFLAGS:               
  CURL LDFLAGS:                
  CURL libraries:              -lcurl
  CXSPARSE CPPFLAGS:           
  CXSPARSE LDFLAGS:            
  CXSPARSE libraries:          -lcxsparse
  DL libraries:                -ldl
  FFTW3 CPPFLAGS:              
  FFTW3 LDFLAGS:               
  FFTW3 libraries:             -lfftw3
  FFTW3F CPPFLAGS:             
  FFTW3F LDFLAGS:              
  FFTW3F libraries:            
  fontconfig CFLAGS:           -I/usr/local/include  
  fontconfig LIBS:             -L/usr/local/lib -lfontconfig  
  FT2_CFLAGS:                  -I/usr/local/include/freetype2 -I/usr/local/include  
  FT2_LIBS:                    -L/usr/local/lib -lfreetype  
  GLPK CPPFLAGS:               
  GLPK LDFLAGS:                
  GLPK libraries:              
  graphics CFLAGS:             -I/usr/local/include -I/usr/local/include/FL/images -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_THREAD_SAFE -D_REENTRANT
  graphics LIBS:               -L/usr/local/lib -lfltk_gl -lGLU -lGL -lfltk -lXext -lXinerama -lpthread -ldl -lm -lX11
  Magick++ CPPFLAGS:           
  Magick++ LDFLAGS:            
  Magick++ libraries:          
  HDF5 CPPFLAGS:               
  HDF5 LDFLAGS:                
  HDF5 libraries:              
  LAPACK libraries:            -llapack
  OPENGL libraries:            -L/usr/local/lib -lfontconfig   -lGL -lGLU
  PTHREAD flags:               -pthread
  PTHREAD libraries:           
  QHULL CPPFLAGS:              
  QHULL LDFLAGS:               
  QHULL libraries:             -lqhull
  QRUPDATE libraries:          -lqrupdate
  READLINE libraries:          -lreadline
  REGEX libraries:             -L/usr/lib/x86_64-linux-gnu -lpcre
  TERM libraries:              -lncurses
  UMFPACK libraries:           -lumfpack
  X11 include flags:           
  X11 libraries:               -lX11
  Z CPPFLAGS:                  
  Z LDFLAGS:                   
  Z libraries:                 -lz

  Default pager:               less
  gnuplot:                     gnuplot

  Do internal array bounds checking:  false
  Use octave_allocator:               false
  Build static libraries:             false
  Build shared libraries:             true
  Dynamic Linking:                    true (dlopen)
  Include support for GNU readline:   true
  64-bit array dims and indexing:     false

configure: WARNING: GLPK library not found.  The glpk function for solving linear programs will be disabled.
configure: WARNING: GraphicsMagick++ library not found.  The imread function for reading image files will not be fully functional.
configure: WARNING: HDF5 library not found.  Octave will not be able to save or load HDF5 data files.
configure: WARNING: I didn't find texi2dvi, but it's only a problem if you need to reconstruct the DVI version of the manual
configure: 
configure: NOTE: libraries may be skipped if a library is not found OR
configure: NOTE: if the library on your system is missing required features.
_________________________________________________________________________________


Now, regarding the warnings. I know that I have installed all three of those libraries. The GLPK, GraphicsMagick++, and HDF5, respectively. After reading the installation 
instructions and recommendations that came with each package, I went to each website given and downloaded and then installed each library.

It could be that some feature of each is not updated or that I did not install the correct version of the packages. But I did follow the instructions included with ocatve-3.6.4 tarball in terms of the websites provided for the tools recommended.

Additionally, I did install a library from the software center associated with "texi2dvi". It could be that that was also outdated. I could not fing any other with the same name.

Furthermore, you may have noticed above in the output for the "aptitude" command that it is written "Conflicts: octave3.2, octave3.2, octave". However, I do not 
remember ever installing any other versions of gnu octave. And I have used the "locate" command to verify this. 

Now, I have updated my system many times with sudo apt-get update while having gone through at least 5 times the instructions for each of the packages listed in the warnings. 

Basically, I am stuck.

I tried to figure it out myself, as I have done before with my beautiful system, but this time I guess I went above my level.

Any suggestions?

Let me know if I have provided enough information for us to solve this one.. . . .

---

