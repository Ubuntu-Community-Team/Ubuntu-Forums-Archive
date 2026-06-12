---
title: "my problem with: install intel fortran compiler on ubuntu"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by marabsalmani on 2013-11-21
Hi,

I am trying to install fortran in ubuntu. I have followed the instructions given in [http://ubuntuforums.org/showthread.php?t=1082782](http://ubuntuforums.org/showthread.php?t=1082782), but I am facing some problems. The first one is when I try the step 1, which is "sudo apt-get install rpm build-essential". The result is as following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 acroread:i386 : Depends: acroread-bin:i386 but it is not going to be installed
 rpm : Depends: librpm2 (>= 4.9.0) but it is not going to be installed
       Depends: librpmbuild2 (>= 4.9.0) but it is not going to be installed
       Depends: librpmio2 (>= 4.9.0) but it is not going to be installed
       Depends: librpmsign0 (>= 4.9.0) but it is not going to be installed
       Depends: rpm2cpio
       Depends: rpm-common (= 4.9.1.1-1ubuntu0.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

May you please help me to solve this problem?

---

### Post by ubfan1 on 2013-11-21
Did you run sudo apt-get update  before you tried the installs?
That might help.

---

### Post by steeldriver on 2013-11-21
Any particular reason you need *Intel *Fortran? you can easily install GNU gfortran

---

### Post by marabsalmani on 2013-11-21
[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1256996")[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1627500")Dear Ubfan1 and Steeldrive,

Thank you very much.
It turend out that my acroread:i386 installation had created the problem. Once I removed it, I could easily install gfortran. 

Thanks again.

---

