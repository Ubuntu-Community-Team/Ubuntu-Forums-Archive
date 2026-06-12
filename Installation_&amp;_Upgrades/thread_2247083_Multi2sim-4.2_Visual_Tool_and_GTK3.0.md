---
title: "Multi2sim-4.2 Visual Tool and GTK3.0"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by sunny14 on 2014-10-05
Good afternoon guys

I am using Ubuntu 12.0.4 and I have installed libgtk-3-dev, yet when I try to run the multi2sim-4.2 visual tool it says that it does not find GTK support:

[FONT=arial]"Multi2Sim was compiled without support for GTK applications. When you ran[/FONT]
[FONT=arial]    the './configure' script, no GTK support was detected in your system, so[/FONT]
[FONT=arial]    the simulator compilation did not include the visualization tool. To[/FONT]
[FONT=arial]    install it, please follow these steps:[/FONT]
[FONT=arial]      1) Install the development packages for GTK 3.0. Under Debian-based[/FONT]
[FONT=arial]         Linux distributions, this package is listed as 'libgtk-3-dev'.[/FONT]
[FONT=arial]      2) Re-run the './configure' script[/FONT]
[FONT=arial]      3) Recompile the simulator: make clean && make"

I am using the following command to run the visual tool : [/FONT]m2s --visual trace.gz[FONT=arial]
[/FONT]
I re-ran the configure script and make and make install, and tried again, but i still keep getting this error

Any help is appreciated :)

---

### Post by T.J. on 2014-10-06
At a first guess, you are trying to compile multisim yourself and the configure/linker is not finding the library or the header files, yes?  I am assuming you are in asking this question.  If not, you may simply have a bad package. If this does not fix your problem please post back here and I'll work with you to track down the cause.


Have you tried cleaning the source tree aka *make clean* and then an *sudo ldconfig /usr/lib* before rerunning the configure script?  If you don't, you are recycling the object files previously compiled.  This is very important.  Under no circumstances follow the advice of people to change the LD_LIBRARY_PATH unless you fully understand what that does.

---

