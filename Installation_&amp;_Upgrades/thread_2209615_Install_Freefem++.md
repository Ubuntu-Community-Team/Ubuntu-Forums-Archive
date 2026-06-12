---
title: "Install Freefem++"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by Schnipp on 2014-03-06
Hi everyone,

I'm trying to install Freefem++ on my computer, 

The readme file says I am to do:

./configure 
  make 
  make check    (to test de version)
  make install  (under root)

But, when I tryed it, it didn't worked!

Could you help me please?

Thank you,

Schnipp

PS: This message can contain some mistakes :(, I beg you to forgive me for that, I am not a native english speaker...

---

### Post by Schnipp on 2014-03-06
When I try ./configure : 

schnipp@schnipp-Aspire-V3-571:~/ff++$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/schnipp/ff++/missing: Unknown `--is-lightweight' option
Try `/home/schnipp/ff++/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
./configure: line 3666: test: !=: unary operator expected
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for m4... yes
checking for bison... yes
checking for patch... yes
checking for gfortran... gfortran
checking whether we are using the GNU Fortran compiler... yes
checking whether gfortran accepts -g... yes
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to get verbose linking output from gfortran... -v
checking for Fortran 77 libraries of gfortran...  -L/usr/lib/gcc/x86_64-linux-gnu/4.8 -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../.. -lgfortran -lm -lquadmath
configure: WARNING:   get dir of -lgfortran  FLIBS :  /usr/lib/gcc/x86_64-linux-gnu/4.8/libgfortran.so 
checking  Size of fortran 77 integer ...            4
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... lower case, underscore, no extra underscore
configure:     ++ add f77 : /usr/lib/gcc/x86_64-linux-gnu/4.8/libgfortran.so -DAdd_  in  examples++-load/WHERE_LIBRARY-config "
configure:     ++ add fc : /usr/lib/gcc/x86_64-linux-gnu/4.8/libgfortran.so -DAdd_  in  examples++-load/WHERE_LIBRARY-config "
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... none needed
checking whether yytext is a pointer... no
checking for bison... bison -y
checking for pthread_create in -lpthread... yes
configure:     ++ add pthread : -lpthread  in  examples++-load/WHERE_LIBRARY-config "
checking wether we are on a MacIntosh... no
checking wether we are on  SunOS... no
checking wether we are on Microsoft Windows... no
checking prefix dir freefem++  ... /usr/local/lib/ff++/3.28-1
checking whether to generate debugging information... no
checking whether the C compiler accepts -O3... yes
checking whether the C++ compiler accepts -O3... yes
checking whether the Fortran 77 compiler accepts -O3... yes
checking whether the C compiler accepts -mmmx... yes
checking whether the C++ compiler accepts -mmmx... yes
checking whether the Fortran 77 compiler accepts -mmmx... yes
checking whether the C compiler accepts -msse... yes
checking whether the C++ compiler accepts -msse... yes
checking whether the Fortran 77 compiler accepts -msse... yes
checking whether the C compiler accepts -msse2... yes
checking whether the C++ compiler accepts -msse2... yes
checking whether the Fortran 77 compiler accepts -msse2... yes
checking suffix to add to package name... none
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
checking OpenGL/gl.h usability... no
checking OpenGL/gl.h presence... no
checking for OpenGL/gl.h... no
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GLUT/glut.h usability... no
checking GLUT/glut.h presence... no
checking for GLUT/glut.h... no
checking GL/glut.h usability... yes
checking GL/glut.h presence... yes
checking for GL/glut.h... yes
checking add suffix  ... yes
checking for MPIRUN... checking for mpirun... /usr/bin/mpirun
/usr/bin/mpirun
checking for mpipath ... 
checking for mpic++... /usr/bin/mpic++
checking for MPICXX... yes
checking MPI_DOUBLE_COMPLEX... yes
checking for mpif90... /usr/bin/mpif90
checking for mpif90... /usr/bin/mpif90
./configure: line 11709: -show: command not found
ls: cannot access thread/libmpi.*: No such file or directory
ls: cannot access mpi_cxx/libmpi.*: No such file or directory
ls: cannot access mpi/libmpi.*: No such file or directory
ls: cannot access open-rte/libmpi.*: No such file or directory
ls: cannot access open-pal/libmpi.*: No such file or directory
ls: cannot access dl/libmpi.*: No such file or directory
ls: unrecognized option '--export-dynamic/libmpi.*'
Try 'ls --help' for more information.
ls: cannot access nsl/libmpi.*: No such file or directory
ls: cannot access util/libmpi.*: No such file or directory
ls: cannot access m/libmpi.*: No such file or directory
ls: cannot access dl/libmpi.*: No such file or directory
ls: cannot access /usr/lib]/libmpi.*: No such file or directory
checking for mpicc... /usr/bin/mpicc
configure:     ++ add mpifc : -pthread -L/usr/lib/openmpi/lib -lmpi_f90 -lmpi_f77 -lmpi -lopen-rte -lopen-pal -ldl -Wl,--export-dynamic -lnsl -lutil -lm -ldl  -I/usr/lib/openmpi/include -I/usr/lib/openmpi/include/openmpi  in  examples++-load/WHERE_LIBRARY-config "
configure:     ++ add mpif77 : -pthread -L/usr/lib/openmpi/lib -lmpi_f90 -lmpi_f77 -lmpi -lopen-rte -lopen-pal -ldl -Wl,--export-dynamic -lnsl -lutil -lm -ldl  -I/usr/lib/openmpi/include -I/usr/lib/openmpi/include/openmpi  in  examples++-load/WHERE_LIBRARY-config "
configure:     ++ add mpi : -pthread -L/usr/lib/openmpi/lib -lmpi_cxx -lmpi -lopen-rte -lopen-pal -ldl -Wl,--export-dynamic -lnsl -lutil -lm -ldl  -I/usr/lib/openmpi/include -I/usr/lib/openmpi/include/openmpi  in  examples++-load/WHERE_LIBRARY-config "
checking for wget... yes
checking for arit_zero in -lcadnafree... no
checking /home/schnipp/ff++/download/cadna/cadnafree.h usability... no
checking /home/schnipp/ff++/download/cadna/cadnafree.h presence... no
checking for /home/schnipp/ff++/download/cadna/cadnafree.h... no
configure:  without cadna ***** 
checking for fftw_execute in -lfftw3... no
checking fftw3.h usability... no
checking fftw3.h presence... no
checking for fftw3.h... no
checking for tetrahedralize in -ltet... no
checking tetgen.h usability... no
checking tetgen.h presence... no
checking for tetgen.h... no
checking whether the C compiler accepts -mkl... no
checking for MKL...    root:  , arch:  ,  ...  
checking for daxpy_ in -framework vecLib... no
checking for daxpy_ in ... no
checking for daxpy_ in -lblas... yes
checking for blas_zdotu_sub in -lblas... yes
checking cblas.h usability... yes
checking cblas.h presence... yes
checking for cblas.h... yes
checking vecLib/cblas.h usability... no
checking vecLib/cblas.h presence... no
checking for vecLib/cblas.h... no
checking atlas/cblas.h usability... no
checking atlas/cblas.h presence... no
checking for atlas/cblas.h... no
configure:     ++ add blas : -lblas  in  examples++-load/WHERE_LIBRARY-config "
checking for lapack in  /usr/lib/gcc/x86_64-linux-gnu/4.8/libgfortran.so, -lblas and -llapack ... yes
checking for dsaupd_ in -larpack... yes
configure:     ++ add arpack : -larpack -llapack  in  examples++-load/WHERE_LIBRARY-config "
configure:     ++ add lapack : -llapack  in  examples++-load/WHERE_LIBRARY-config "
checking umfpack.h usability... no
checking umfpack.h presence... no
checking for umfpack.h... no
checking umfpack/umfpack.h usability... no
checking umfpack/umfpack.h presence... no
checking for umfpack/umfpack.h... no
checking ufsparse/umfpack.h usability... no
checking ufsparse/umfpack.h presence... no
checking for ufsparse/umfpack.h... no
checking suitesparse/umfpack.h usability... yes
checking suitesparse/umfpack.h presence... yes
checking for suitesparse/umfpack.h... yes
checking for amd_info in -lamd... yes
checking for cholmod_add in -lcholmod... yes
checking for colamd_set_defaults in -lcolamd... yes
checking for umf_i_malloc in -lumfpack... yes
configure:     ++ add amd : -lumfpack  -lamd -lcholmod -lcolamd -I/usr/include/suitesparse in  examples++-load/WHERE_LIBRARY-config "
configure:     ++ add umfpack : -lumfpack  -lamd -lcholmod -lcolamd -I/usr/include/suitesparse in  examples++-load/WHERE_LIBRARY-config "
checking for times... yes
checking for sysconf... yes
checking for unistd.h... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for asinh... yes
checking for acosh... yes
checking for atanh... yes
checking for getenv... yes
checking for jn... yes
checking for erfc... yes
checking for tgamma... yes
checking for gettimeofday... yes
checking for srandomdev... no
checking for second_... no
checking for libtool... no
checking for dlfcn.h... yes
checking for sin in -lm... yes
checking for dlinfo in -ldl... yes
checking whether dlopen links ok... yes
checking whether the C++ compiler accepts -rdynamic... yes
checking whether the C++ compiler accepts -fPIC... yes
checking whether the C compiler accepts -fPIC... yes
checking whether the C compiler accepts -fPIC... yes
checking whether the Fortran compiler accepts -fPIC... yes
checking whether the Fortran compiler accepts -fPIC... yes
checking whether the Fortran compiler accepts -fPIC... yes
checking whether the Fortran compiler accepts -fPIC... yes
checking for latex... yes
checking for makeindex... yes
checking for dvips... yes
checking for pdf2ps... yes
checking for epstopdf... epstopdf
checking for convert... yes
checking for gzip... yes
checking for pdflatex... yes
./configure: line 16241: test: =: unary operator expected
checking kernel version... 3.11.0
checking libc version... libc-2.17
checking check mumps... no
checking check mumps_ptscotch... no
checking check mumps_scotch... no
checking check hypre... no
checking check fftw3... no
checking check superlu_dist... no
checking check superlu... no
checking check Superlu4... no
checking check blacs... no
checking check scalapack... no
checking check scotch... no
checking check ptscotch... no
checking check metis... no
checking check parmetis... no
checking check freeyams... no
checking check mmg3d... no
checking check mshmet... no
checking check gsl... no
checking check parms... no
checking check tetgen... no
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating download/Makefile
config.status: creating download/blas/Makefile
config.status: creating download/arpack/Makefile
config.status: creating download/umfpack/Makefile
config.status: creating download/fftw/Makefile
config.status: creating src/Makefile
config.status: creating src/bamglib/Makefile
config.status: creating src/Graphics/Makefile
config.status: creating src/femlib/Makefile
config.status: creating src/Algo/Makefile
config.status: creating src/lglib/Makefile
config.status: creating src/fflib/Makefile
config.status: creating src/nw/Makefile
config.status: creating src/mpi/Makefile
config.status: creating src/bamg/Makefile
config.status: creating src/libMesh/Makefile
config.status: creating src/medit/Makefile
config.status: creating src/bin-win32/Makefile
config.status: creating examples++/Makefile
config.status: creating examples++-eigen/Makefile
config.status: creating examples++-tutorial/Makefile
config.status: creating examples++-mpi/Makefile
config.status: creating examples++-load/Makefile
config.status: creating examples++-chapt3/Makefile
config.status: creating examples++-bug/Makefile
config.status: creating examples++-other/Makefile
config.status: creating examples++-3d/Makefile
config.status: creating DOC/Makefile
config.status: creating config.h
config.status: executing depfiles commands
configure:   freefem++ used  download :  
configure:           --  Dynamic load facility: yes 
configure:          --  ARPACK (eigen value): yes 
configure:          --  UMFPACK (sparse solver) yes 
configure:          --  BLAS yes 
configure:          --  with MPI             yes
configure:     progs: FreeFem++-nw bamg cvmsh2  FreeFem++-mpi ffmedit ffglut

---

