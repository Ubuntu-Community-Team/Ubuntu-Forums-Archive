---
title: "gromacs installation error: make: No targets specified and no makefile found."
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by Shalini_Sinha on 2016-05-16
I m trying to install gromacs 5.1.2 on ubuntu 14.04.
When I try to run "make", it shows this warning, 

make: *** No targets specified and no makefile found.  Stop.

I am just a newbie, I looked up for solutions in few places. 
I tried running "./configure".

It shows that there is no such file and directory.

I have installed the following required dependencies.
sudo apt-get install libqt4-dev
sudo apt-get install libjack0
sudo apt-get install libjack-dev
sudo apt-get install libasound2-dev
sudo apt-get install libsndfile1-dev

But still it shows the same error with "./configure"

Please look into this matter. Thank you in advance.:P

---

### Post by steeldriver on 2016-05-16
It uses cmake - see [Introduction to building GROMACS](http://manual.gromacs.org/documentation/5.1.2/install-guide/index.html#introduction-to-building-gromacs)

---

