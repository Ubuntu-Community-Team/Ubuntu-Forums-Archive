---
title: "Help me on installing octave!"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by ogro0 on 2010-08-25
Hello!

Iam using ubuntu 10.4 and iam having issues while trying to install octave 3.2.4.
I followed the guide that comes with the .tar archive, but I just cant complete the installation.

I see some errors like 

"checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran 77 libraries of ... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... configure: error: in `/home/ogro0/octave-3.2.4':
configure: error: cannot compile a simple Fortran program
See `config.log' for more details."




and when I tried to 'make', or 'make install', appears that I have to download some archives, but I guess I already have em.

please help me, and sorry about my bad english.

---

### Post by dv3500ea on 2010-08-25
Unless you desperately need the latest version of octave, install the package [octave3.2]("apt:octave3.2").
You can use Ubuntu Software Centre or Synaptic Package Manager to do this.

---

### Post by ogro0 on 2010-08-25
thanks man! that helped me

ty

---

### Post by marrabld on 2011-05-08
If you do wan't to install octave 3.4 (for its many improvements) you need the fortran compilers (not sure which one either f2c or gfortran) and the BLAS and LAPACK libraries

```
sudo apt-get install f2c gfortran libblas-dev liblapack-dev
```

should do it.

---

### Post by Luz77 on 2012-03-05
> **marrabld said:**
> ```
sudo apt-get install f2c gfortran libblas-dev liblapack-dev
```
Thanks a lot!

I also had to install, for octave 3.4.3:
```
sudo apt-get install libpcre3-dev libreadline-dev
```

---

