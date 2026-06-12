---
title: "System call under Linux, gfortran v4.4.5"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Maffie on 2011-02-01
I am building a model which should be portable to any possible platform (I use ubuntu 10.10 i686 Linux, with gcc 4.4.5 compiler).  Unfortunately, the support for gfortran users is limited, so that is why 
I try to ask my question here.

There is a script that used the system() command.
Now, as a (g)fortran newbie, I am not exactly sure what it does, and 
definitely not how to define it for my linux environment.

In my example:

public :: shr_sys_system  ! make a system call
public :: shr_sys_chdir   ! change current working dir
public :: shr_sys_getenv  ! get an environment variable
public :: shr_sys_abort   ! abort a program
public :: shr_sys_irtc    ! returns real-time clock tick
public :: shr_sys_sleep   ! have program sleep for a while
public :: shr_sys_flush   ! flush an i/o buffer

in which a subroutine is configured as follows (e.g. for shr_sys_system):
SUBROUTINE shr_sys_system(str,rcode)

    IMPLICIT none

    !----- arguments ---
    character(*)        ,intent(in)  :: str    ! system/shell command string
    integer(SHR_KIND_IN),intent(out) :: rcode  ! function return error code

    !----- functions -----
#if (defined CRAY) || (defined UNICOSMP)
    integer(SHR_KIND_IN),external    :: ishell ! function to envoke 
shell command
#endif
#if (defined OSF1 || defined SUNOS || (defined LINUX && !defined 
__G95__) || (defined LINUX && !defined CATAMOUNT))
    integer(SHR_KIND_IN),external    :: system ! function to envoke 
shell command
#endif

    !----- local -----
#if (defined CATAMOUNT)
    character(2*SHR_KIND_CL) :: file1            ! one or two filenames
    character(  SHR_KIND_CL) :: file2            ! 2nd file name
    integer(SHR_KIND_IN)     :: iloc             ! index/location within 
a string
#endif

    !----- formats -----
    character(*),parameter :: subName =   '(shr_sys_system) '
    character(*),parameter :: F00     = "('(shr_sys_system) ',4a)"

!-------------------------------------------------------------------------------
! PURPOSE: an architecture independant system call
! NOTE:
! - for Catamount (Cray, pheonix at ORNL) there is no system call -- 
workarounds
!   exist only for simple "rm" and "cp" commands
!-------------------------------------------------------------------------------


In the last part, there are some calls dependent on my system (my case = 
Linux):
#if (defined CRAY) || (defined UNICOSMP)
    rcode=ishell(str)
#endif

#if (defined IRIX64 || defined NEC_SX)
    rcode = 0
    call system(str)
#endif

#if (defined AIX)
    call system(str,rcode)
#endif

#if (defined OSF1 || defined SUNOS || defined LINUX && !defined 
CATAMOUNT || defined __G95__)
    rcode = SYSTEM(str)
#endif

#if (!defined CRAY && !defined IRIX64 && !defined AIX && !defined OSF1 
&& !defined SUNOS && !defined LINUX && !defined NEC_SX && !defined 
UNICOSMP && !defined __G95__)
    write(s_logunit,F00) 'ERROR: no implementation for this architecture'
    call shr_sys_abort(subName//'no implementation for this architecture')
#endif

END SUBROUTINE shr_sys_system

So my question here is how to define the system call exactly for Linux. 
Because as it is now, I get the following error:
/usr/workdir/cesm1_0_2/scripts/test2/lib/libcsm_share.a(shr_sys_mod.o): 
In function `shr_sys_system':
/usr/workdir/cesm1_0_2/models/csm_share/shr/shr_sys_mod.F90:83: 
undefined reference to `system_'

and I can't seem to find a lot of information on this on the web!
Therefore, any help is welcome!

Cheers,
Matthias

---

