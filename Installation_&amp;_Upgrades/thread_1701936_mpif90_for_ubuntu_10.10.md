---
title: "mpif90 for ubuntu 10.10"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by malik_ubd on 2011-03-07
Hi,

 I just installed ubuntu10.10 version (maverick, the latest version). When I wanted to install MPI (Message Passing Interface) complier in the "ubuntu software center", I am not able to find any. 

 I searched for the compiler named "mpif90", but no result fetched. Then I searched for words like mpi and fortran. no result this time too.

 How to get mpif90 for this version of ubuntu 10.10.

Earlier I have installed the earlier version of ubuntu, "Ubuntu 10.04 LTS" in a different machine. Then I had been able to get mpif90 compiler from "ubuntu software center"

Please help me to get it for "Ubuntu 10.10"

Thanks

---

### Post by mwtoews on 2011-05-01
Try:
```
apt-get install libopenmpi-dev
```

This will give you /usr/bin/mpif90.openmpi

---

