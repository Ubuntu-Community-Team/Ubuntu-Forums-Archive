---
title: "Error in executing a C++ code in MAkefile"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by SUMAN003 on 2013-09-15
Hi,

I am facing the following problem while trying to run a C++ code in Makefile. Please suggest a solution to rectify this:[B]

$ make[/B]

ccache g++ -ggdb -fPIC -I/opt/Xilinx/Vivado_HLS/2013.2/Linux_x86_64/tools/systemc/include -I. -I/opt/Xilinx/Vivado_HLS/2013.2/include -mcmodel=medium  -lm -llog4cxx -c quadratic_equation_test.cc
In file included from quadratic_equation_test.cc:7:0:
types.h:4:22: fatal error: ap_fixed.h: No such file or directory
compilation terminated.

---

### Post by steeldriver on 2013-09-15
The ap_fixed.h file is not a system header file, it appears to be part of a 3rd party arbitrary precision library provided by Xilinx / Vivado - either it's not installed, in which case you need to install it, or it's not in a location where the compiler can find it, in which case you need to find where it is located and set your -I include options accordingly.

---

