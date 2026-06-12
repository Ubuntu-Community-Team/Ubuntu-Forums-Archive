---
title: "Matlab 7 R14 Java &amp; OpenGL problems on KDE"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by Cosmic_Desert on 2006-10-06
Hi to all!

well im trying to make matlab 7 R14 run with java support and i take the following:



Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.
Warning: Could not access OpenGL library

                              < M A T L A B >
                  Copyright 1984-2004 The MathWorks, Inc.
                         Version 7.0.0.19901 (R14)
                                May 06, 2004

??? Undefined function or variable 'matlabrc'.



It seems that jre1.4 has been installed properly in $MATLAB/sys/java
and i have installed java in my pc when i type java in my console it answer.Maybe there a linking problem?](*,) 

Additionaly matlab cant see my gl and glu libraries

Any Help??
thanx!!!!

---

### Post by altonese78 on 2006-10-21
you have to run the post install script:

sudo /usr/local/matlab7/install_matlab

---

### Post by rebbo on 2006-10-24
Try starting matlab with "-nojvm" option, I think I have seen something similar on [www.kluid.com](www.kluid.com)

Rebbo

---

