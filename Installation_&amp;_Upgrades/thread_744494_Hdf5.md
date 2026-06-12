---
title: "Hdf5"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by TreeHugger52 on 2008-04-03
Hi- new ubuntu user here, running Gutsy on a Macbook Santa Rosa.

I am attempting to modify a large Fortran 90 program (written by a colleague- I'm new to fortran too) that uses datafiles stored in HDF5 format. The makefile for the gfortran compiler (include.mk.opt.gfortran) references HDF5 libraries on a different machine, so I'm trying to modify the path to point to correct place on my Macbook. I've installed what I think is the correct library package using:

sudo apt-get install libhdf5-serial-1.6.4-0c2


The packaged downloaded and installed nicely, but now I can't find where the library went. Would it be /usr/lib?  How do I find out?

---

### Post by dstew on 2008-04-04
Try **locate libhdf5**.

---

### Post by TreeHugger52 on 2008-04-05
Yep- that did it. Thanks!

I guess I need to learn my linux commands...

---

