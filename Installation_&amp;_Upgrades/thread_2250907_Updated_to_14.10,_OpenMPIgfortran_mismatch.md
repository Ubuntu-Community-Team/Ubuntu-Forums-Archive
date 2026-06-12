---
title: "Updated to 14.10, OpenMPI/gfortran mismatch"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by andrew165 on 2014-10-31
Hi all,

So I just updated my computer to Ubuntu 14.10 from 14.04.  Today, I tried to compile some scientific code (BerkeleyGW for those interested) however I ran into the following issue.  I'm using openmpi and gfortran as installed via the repositories.
The error I get during compiling:
Fatal Error: Cannot read module file 'mpi.mod' opened at (1), because it was created by a different version of GNU Fortran

The current version of gcc/gfortran/etc is 4.9.1.  When I go and look at the mpi.mod file (at /usr/lib/openmpi/lib/mpi.mod), it was created with "GFORTRAN module version '10' created from mpi.f90" which implies gfortran 4.8.

I find it strange that this occurs since both are installed out of the updated utopic respositories.  I tried completely removing openmpi and reinstalling it but the issue still persists.

Does anybody have any suggestions?

Thanks in advance.

---

### Post by roy-stogners on 2015-01-13
My workaround was "sudo apt-get install gfortran-4.8; sudo ln -sf gfortran-4.8 /usr/bin/gfortran".  If you must use gfortran 4.9 I'm not sure there's any solution short of compiling your own MPI.

---

