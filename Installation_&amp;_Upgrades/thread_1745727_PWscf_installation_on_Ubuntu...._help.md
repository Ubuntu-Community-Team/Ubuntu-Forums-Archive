---
title: "PWscf installation on Ubuntu.... help"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by mahdi109 on 2011-05-01
Hi all,

 I am a newbie to Ubuntu. I have been trying to install two quantum computational program, PWscf without success.
1) I needs to have **a fortran compiler. a working fortran-95 compiler.**
2)Libraries: Quantum-ESPRESSO uses and provides a copy of the following external libraries: 
[LIST]
[*]BLAS (Basic Linear Algebra Subroutines):  [http://www.netlib.org/blas](http://www.netlib.org/blas)
[*]LAPACK (Linear Algebra Package):  [http://www.netlib.org/lapack](http://www.netlib.org/lapack)
[*]FFTW (Fast Fourier-Transform package):   [http://www.fftw.org]("http://www.fftw.org/")
[/LIST]

i dont know how to install these.

Thank you in advance,

---

### Post by mahdi109 on 2011-05-06
Please help me ...

---

### Post by aeftimia on 2011-08-11
I have been working for weeks installing quantum chemistry software on ubuntu. I posted an installer script on sourceforge here: [https://sourceforge.net/projects/aeftimiamisc/files/installstuff/](https://sourceforge.net/projects/aeftimiamisc/files/installstuff/)

You can edit the installstuff.sh script to choose what you want to install. Be sure to run it with bash and not sh. The patch is for dacapo, which I am still having some trouble getting to work. Feel free to delete the dacapo installation part of the script at this point.

I would use svn, but I am still very new to this whole opensource processes and cannot figure out how to create a repository on sourceforge.


I am hoping to try to make this script of mine a little more well known (actually, that is what I logged on to do--I did a search for "quantum" to see if I could help anyone in particular first) and save people the time it took me to get this working.

---

### Post by steve11911 on 2011-08-12
Found a few pages that might help including an install tutorial for Quantum-Espresso on Ubuntu.

Installing the Fortran 95 compiler:

[https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)

packages listed here:

[https://launchpad.net/ubuntu/natty/+package/gfortran](https://launchpad.net/ubuntu/natty/+package/gfortran)

PWscf :

The last panel on this page offers 3 links.

[http://www.linux-archive.org/ubuntu-user/549312-pwgui.html](http://www.linux-archive.org/ubuntu-user/549312-pwgui.html)

The first two are good, the third is not-but I found the install tutorial page here:

[http://conquer-ur-computer.blogspot.com/2010/12/install-quantum-espresso-in-ubuntu.html#more](http://conquer-ur-computer.blogspot.com/2010/12/install-quantum-espresso-in-ubuntu.html#more)

LAPACK:

[https://help.ubuntu.com/community/Lapack++](https://help.ubuntu.com/community/Lapack++)

FFTW:

[http://micro.stanford.edu/wiki/Install_FFTW3](http://micro.stanford.edu/wiki/Install_FFTW3)

Of possible interest-A couple pages relating to BLAS:

[https://groups.google.com/group/theano-users/browse_thread/thread/507fda60bdc647f5](https://groups.google.com/group/theano-users/browse_thread/thread/507fda60bdc647f5)

This suggests BLAS is not optimized in natty and suggests SDPA:

[http://sourceforge.net/news/?group_id=407146](http://sourceforge.net/news/?group_id=407146)

For aeftimia - Dacapo:

[https://listserv.fysik.dtu.dk/pipermail/ase-users/2011-March/000969.html](https://listserv.fysik.dtu.dk/pipermail/ase-users/2011-March/000969.html)

For those who may wander here:

[http://www-k3.ijs.si/kokalj/pwgui/](http://www-k3.ijs.si/kokalj/pwgui/)

Whew...

---

