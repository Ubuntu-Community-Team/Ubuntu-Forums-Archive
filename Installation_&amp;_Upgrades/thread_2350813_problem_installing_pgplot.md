---
title: "problem installing pgplot"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by honorableraven on 2017-01-28
Hi everybody,
I am trying to install pgplot on my laptop. I am using the instructions from this site: 
[http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html](http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html)

However, when I come to the last step, and execute the make command, I get this error:

g77 -c -Wall -O /home/soham/Desktop/pgplot/src/pgarro.f
make: g77: Command not found
makefile:109: recipe for target 'pgarro.o' failed
make: *** [pgarro.o] Error 127

I am very new to linux,and have no idea what the problem is. I have gfortran installed, could it be that I need to install some older g77 compiler? Or does this signify that I do not have GCC on my system, and need to download and install it? My laptop runs Ubuntu 16.04 LTS, if that is any help.
Any suggestions will be greatly appreciated. Thanks in advance.

---

### Post by nothingspecial on 2017-01-28
you might need build-essential, f2c and or ratfor

---

### Post by Impavidus on 2017-01-28
pgplot is in the repositories for Ubuntu 16.04. Just run```
sudo apt install pgplot5
```It worked for me, it will give both fortran and C interfaces. libpgplot-perl and ruby-pgplot give two more interfaces.

---

### Post by honorableraven on 2017-01-28
Ok, I will try to look those up, and see if that helps.

---

### Post by honorableraven on 2017-01-28
> **Impavidus said:**
> pgplot is in the repositories for Ubuntu 16.04. Just run```
sudo apt install pgplot5
```It worked for me, it will give both fortran and C interfaces. libpgplot-perl and ruby-pgplot give two more interfaces.

Unfortunately that won't work for me. I have already tried installing pgplot5, but I need it to run ORTEP, an application which has not been updated in a long time. If I try to make my source code of ORTEP with pgplot5, it returns a list of "undefined reference to *" kind of errors.

---

### Post by SeijiSensei on 2017-01-28
Start by installing build-essential so you have a compiler and the like.   If that isn't sufficient to get it to compile, then try
```
sudo apt-get build-dep plplot5
```
and Ubuntu will install any needed development libraries and headers.

---

### Post by steeldriver on 2017-01-28
FWIW it seems to be happy if you configure it for g77_gcc 

```

../src/pgplot/makemake ../src/pgplot linux g77_gcc

```

and then edit the makefile to change g77 to gfortran

```

.
.
.
#
# Fortran compiler and compilation flags
#
[B]FCOMPL=gfortran
[/B]FFLAGC=-u -Wall -fPIC -O
FFLAGD=-fno-backslash
#
# C compiler and compilation flags
#
.
.
.

```

Obviously install gfortran from the repository if you haven't already done so

---

### Post by honorableraven on 2017-01-30
> **steeldriver said:**
> FWIW it seems to be happy if you configure it for g77_gcc 

```

../src/pgplot/makemake ../src/pgplot linux g77_gcc

```

and then edit the makefile to change g77 to gfortran

```

.
.
.
#
# Fortran compiler and compilation flags
#
[B]FCOMPL=gfortran
[/B]FFLAGC=-u -Wall -fPIC -O
FFLAGD=-fno-backslash
#
# C compiler and compilation flags
#
.
.
.

```

Obviously install gfortran from the repository if you haven't already done so

I tried this, and it looked like it would work smoothly, and then suddenly, there was a new error :
makefile:662: recipe for target 'mfdriv.o' failed
make: *** [mfdriv.o] Error 1

Again, I have no idea what's wrong. Can anybody help?

---

### Post by steeldriver on 2017-01-30
Did you edit the drivers.list file? do you specifically need

```

MFDRIV 0 /FILE      PGPLOT graphics metafile

```

If not, comment it out (!) and try again

---

