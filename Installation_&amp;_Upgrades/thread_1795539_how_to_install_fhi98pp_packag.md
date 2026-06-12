---
title: "how to install fhi98pp packag ?????"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by mahdi109 on 2011-07-02
dear all
I'm trying to install the fhi98pp packag.
but i dont understand this Instructions:

```
a) Customize "Makefile" in "./src". You need to set compiler and linker flags
   compatible to your platform. Some linear algebra package is required, and
   you need to specify either use of the ESSL library or the libFREE library 
   (an excerpt of the LAPACK package put into "./lib").

b) If libFREE is used make should take automatically care of generating and
   linking this library. Alternatively go to "./lib" and create the archive 
   "libFree.a" using <make -f make.libFree>. Again you need to set appropriate 
   compiler flags in "make.libFree" first. 

c) In "/src" create the executables
   "./src/fhipp.x" ... pseudopotential generating by <make fhipp.x>
   "./src/pslp.x" .... pseudopotential generating by <make pslp.x>
   If linking the library fails, the respective syntax for linking in 
   the present "Makefile" might be incompatible with your platform. 
   Corrections shoud be straightforward, however linking the objects
   by hand is an alternative too.
   
d) Set appropriate paths for executables and graphics header files etc. in the
   shell scripts "psgen" and "pswatch" (stored in ./bin/Tools). This can be
   done by specifying the environment variable "FHIPP_PATH" which should point
   to the directory fhi98PP.
   For a list of the shell scripts' options enter <psgen -h> and <pswatch -h>.

e) Verify that you can reproduce the results of the sample run given in
   "./sample".

```


**please help me..**

---

### Post by aeftimia on 2011-08-19
I know this is not an answer to your question, but it could be a solution to your problem nonetheless. I have installed a different pseudopotential generator called APE with the following set of commands:

apt-get -y install libscalapack-mpi1 libscalapack-mpi-dev gfortran etsf-io libetsf-io-dev netcdf-bin libnetcdf-dev libsparskit-dev libsparskit2.0 libatlas-dev libatlas-base-dev gsl-bin libgsl0-dev libblas-dev liblapack-dev

cd /opt
svn co [http://www.tddft.org/svn/octopus/branches/4.0.x/libxc](http://www.tddft.org/svn/octopus/branches/4.0.x/libxc) libxc
cd libxc
autoreconf -i
./configure
make all
make install

cd /opt
name=ape-1.1.1.tar.gz
wget http://www.tddft.org/programs/APE/sites/default/files/$name
mkdir ape
tar zxvf $name --strip=1 -C ape
rm -f $name
cd ape
autoreconf -i
./configure --prefix=/usr/local --with-libxc-prefix=/opt/etsf
make all
make install

you can just copy and paste them into terminal as long as you are running it as root--just type sudo su first and put in your password.)

I mention you might not need all of the stuff installed from apt-get, but I am pretty sure that covers it. The stuff you do not need is useful for installing other common quantum chemistry software anyway, and probably will not hurt to have around. I have a script that installs a whole bunch of popular quantum chemistry software (that I have been trying to circulate to save others the weeks it took me to get it all up and running):
[https://sourceforge.net/projects/aeftimiamisc/files/installstuff/](https://sourceforge.net/projects/aeftimiamisc/files/installstuff/)

It includes APE in the set of software it installs. 

I know that did not answer your original question, but I hope it solved the problem.

---

### Post by steve11911 on 2011-08-20
There is an installation instruction at the bottom of this page:

[http://www.etsf.eu/resources/software/etsf_software_repository](http://www.etsf.eu/resources/software/etsf_software_repository)


This forum link stands a good chance of getting you some help:

[http://imechanica.org/node/1394](http://imechanica.org/node/1394)

---

