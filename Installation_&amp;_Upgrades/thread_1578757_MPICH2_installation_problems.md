---
title: "MPICH2 installation problems"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by peppermandjm on 2010-09-20
Hi.  I am currently running Lucid x86 (this was upgraded from Jaunty last May) on my Acer Extensa 4630Z in a dual boot config with Vista.  I am still kind of new to linux, so the issue could be something simple (I have been using it for about a year now, but I don't use it on an every day basis) and my primary use of it is for programming.  Long story short is I need to install MPICH2 for a project I am starting, but I'm having trouble installing it.  The version I'm trying to install is 1.2.1.  Here's the sequence of commands I enter:
> 
wget -O /mpi2/mpich2-1.2.1.tar.gz [http://www.mcs.anl.gov/research/projects/mpich2/downloads/tarballs/1.2.1/mpich2-1.2.1.tar.gz](http://www.mcs.anl.gov/research/projects/mpich2/downloads/tarballs/1.2.1/mpich2-1.2.1.tar.gz) 

sudo tar zxv --file /mpi2/mpich2-1.2.1.tar.gz --directory /mpi2

cd /mpi2/mpich2-1.2.1

export CC=gcc 
export CXX=g++ 
export F77=gfortran 
export FC=gfortran 
export F90=gfortran 

export MPI2_PREFIX=/mpi2/mpich2-1.2.1/gcc

sudo ./configure --prefix=${MPI2_PREFIX} 2>&1 | sudo tee configure.log
       
sudo make 2>&1 | sudo tee make.log

sudo make install 2>&1 | sudo tee make.install.log

sudo make installcheck 2>&1 | sudo tee make.installcheck.logI get errors in the make installcheck, starting here:

.....
*** Test C program with the MPI tracing library .......................... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 cpi_trace
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

*** Test C program with the MPI logging library .......................... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 cpi_log
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

*** Test C program with the MPI and manual logging libraries ............. No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 cpilog
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

Running installation runtest for Fortran logging program...

*** Test F77 program with the MPI and manual logging libraries ........... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 fpilog
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

Running installation runtest for C graphics program...

*** Test C program with the MPI animation library ........................ No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 cpi_anim
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

*** Test C program with the X11 graphics library ......................... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 cxgraphics
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

Running installation runtest for Fortran graphics program...

*** Test F77 program with the X11 graphics library ....................... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 fxgraphics
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

Running installation runtest for C collchk program...

*** Test C program with the MPI collective/datatype checking library ..... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 wrong_int_byte
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

Running installation runtest for Fortran collchk program...

*** Test F77 program with the MPI collective/datatype checking library ... No.
    The failed command is :
/mpi2/mpich2-1.2.1/gcc/bin/mpiexec -n 4 wrong_reals
/mpi2/mpich2-1.2.1/gcc/bin/mpdroot: open failed for root's mpd conf filempiexec_<laptop_name> (__init__ 1208 ): forked process failed; status=255

(if you need a complete log, or any other info, just ask-I didn't want to post it if it wasn't necessary as its quite long).

Thank you for your time,

-Dave

---

