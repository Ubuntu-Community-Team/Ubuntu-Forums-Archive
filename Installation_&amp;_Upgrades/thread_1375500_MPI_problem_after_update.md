---
title: "MPI problem after update"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by florian100 on 2010-01-08
Hi everyone
I run an update of ubuntu 9.10 on my laptop and now my mpi programs do not work anymore... The error is


[florian-laptop:02935] [[INVALID],INVALID] ORTE_ERROR_LOG: A system-required executable either could not be found or was not executable by this user in file ../../../../../../orte/mca/ess/singleton/ess_singleton_module.c at line 269
[florian-laptop:02935] [[INVALID],INVALID] ORTE_ERROR_LOG: A system-required executable either could not be found or was not executable by this user in file ../../../../../../orte/mca/ess/singleton/ess_singleton_module.c at line 143
[florian-laptop:02935] [[INVALID],INVALID] ORTE_ERROR_LOG: A system-required executable either could not be found or was not executable by this user in file ../../../orte/runtime/orte_init.c at line 132
--------------------------------------------------------------------------
It looks like orte_init failed for some reason; your parallel process is
likely to abort.  There are many reasons that a parallel process can
fail during orte_init; some of which are due to configuration or
environment problems.  This failure appears to be an internal failure;
here's some additional information (which may only be relevant to an
Open MPI developer):

  orte_ess_set_name failed
  --> Returned value A system-required executable either could not be found or was not executable by this user (-127) instead of ORTE_SUCCESS
--------------------------------------------------------------------------
--------------------------------------------------------------------------
It looks like MPI_INIT failed for some reason; your parallel process is
likely to abort.  There are many reasons that a parallel process can
fail during MPI_INIT; some of which are due to configuration or environment
problems.  This failure appears to be an internal failure; here's some
additional information (which may only be relevant to an Open MPI
developer):

  ompi_mpi_init: orte_init failed
  --> Returned "A system-required executable either could not be found or was not executable by this user" (-127) instead of "Success" (0)
--------------------------------------------------------------------------
*** An error occurred in MPI_Init
*** before MPI was initialized
*** MPI_ERRORS_ARE_FATAL (your MPI job will now abort)
[florian-laptop:2935] Abort before MPI_INIT completed successfully; not able to guarantee that all other processes were killed!

I have not really an idea what causes this problem but is definitely a problem of the mpi package because the mpi programs are working on other machines...
My MPI program is using MPI only, not openMP
I am thankful for any help, if any additional informations are needed I am happy to provide them
best regards
florian

---

### Post by sheehan on 2010-01-12
Hi, I had a similar problem, following the suggestion here
[https://answers.launchpad.net/dorsal/+question/91701](https://answers.launchpad.net/dorsal/+question/91701)
to compile and install openmpi from source fixed it for me.

---

### Post by Adversus on 2010-01-26
Had the same problem. Got around it by removing openmpi and using the lam mpi package.

---

### Post by sina.moeini@gmail.com on 2011-12-24
had the same problem, was solved after installing the the package openmpi-bin

apt-get install openmpi-bin

---

