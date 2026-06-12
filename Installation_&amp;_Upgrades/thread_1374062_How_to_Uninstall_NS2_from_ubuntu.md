---
title: "How to Uninstall NS2 from ubuntu?"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by mharis on 2010-01-06
Hi,

I installed NS2.34 allinone a few days ago. The installation was successfull but the package didnt help me out because it doesnt have any support for RSVP. I need to install older NS2 2.26 which can be extended with an MNS patch for RSVP. How do i uninstall NS2.34 allinone so that i can be able to install the older version?? 

I installed NS2.34 by using the following procedure:
(i had already downloaded the tar package)

-----------------------------------------------------------------

$ sudo apt-get install build-essential autoconf automake libxmu-dev
$ ./install
$ export CC=gcc-4.3


 $ gedit ~/.bashrc 

# LD_LIBRARY_PATH
OTCL_LIB=/your/path/ns-allinone-2.34/otcl-1.13
NS2_LIB=/your/path/ns-allinone-2.34/lib
X11_LIB=/usr/X11R6/lib
USR_LOCAL_LIB=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB:$X11_LIB:$USR_LOCAL_LIB

# TCL_LIBRARY
TCL_LIB=/your/path/ns-allinone-2.34/tcl8.4.18/library
USR_LIB=/usr/lib
export TCL_LIBRARY=$TCL_LIB:$USR_LIB

# PATH
XGRAPH=/your/path/ns-allinone-2.34/bin:/your/path/ns-allinone-2.34/tcl8.4.18/unix:/your/path/ns-allinone-2.34/tk8.4.18/unix
NS=/your/path/ns-allinone-2.34/ns-2.34/
NAM=/your/path/ns-allinone-2.34/nam-1.14/
PATH=$PATH:$XGRAPH:$NS:$NAM


 $ source ~/.bashrc

$ cd ns-2.34
$ ./validate


All the steps were successful.

Thanks and Regards :)

---

### Post by mharis on 2010-01-06
Well I really need some help coz I have to take my work for demo tomorrow!! :(

---

