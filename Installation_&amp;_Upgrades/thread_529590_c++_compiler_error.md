---
title: "c++ compiler error"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by damansandhu on 2007-08-19
hi , i am using kubuntyu 7.04 and i am getting this error when i try to run GNU C Compiler.

daman@Ultimate:~$ gcc
gcc: no input files
daman@Ultimate:~$

---

### Post by Pumalite on 2007-08-19
sudo apt-get install build-essential

---

### Post by damansandhu on 2007-08-19
daman@Ultimate:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libberylsettings0-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daman@Ultimate:~$ gcc
gcc: no input files
daman@Ultimate:~$

---

### Post by bazcor on 2007-08-19
GCC requires an input file to compile for example:

daman@Ultimate:~$ gcc ./myprog.c

or
daman@Ultimate:~$ gcc ./myprog.cpp


gcc ---help for all options

---

