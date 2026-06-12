---
title: "bash: :/usr/X11R6/lib:/usr/local/lib: No such file or directory   What to do?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by adilodha on 2010-04-01
hi,
i got this message --> "bash: :/usr/X11R6/lib:/usr/local/lib: No such file or directory", when i tried to run 

"source ~/.bashrc"

after installation of ns-allinone-2.34 on ubuntu 9.04.

what to do?
please help me..

---

### Post by rejuvenate on 2010-04-06
can you post the contents of the .bashrc file....

---

### Post by affus56 on 2011-04-23
.bahsrc file
please how to get rid of this problem

#LD_LIBRARY_PATH

OTCL_LIB=/home/sadaq/ns-allinone-2.33/otcl-1.13
NS2_LIB=/home/sadaq/ns-allinone-2.33/lib
X11_LIB=/usr/X11R6/lib
USR_LOCAL_LIB=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB
:$X11_LIB:$USR_LOCAL_LIB

# TCL_LIBRARY

TCL_LIB=/home/sadaq/ns-allinone-2.33/tcl8.4.18/library
USR_LIB=/usr/lib
export TCL_LIBRARY=$TCL_LIB:$USR_LIB

# PATH

XGRAPH=/home/sadaq/ns-allinone-2.33/bin:/home/sadaq/ns-allinone-2.33/tcl8.4.18/unix:/home/sadaq/ns-allinone-2.33/tk8.4.18/unix:/home/sadaq/ns-allinone-2.33/xgraph-12.1/
NS=/home/sadaq/ns-allinone-2.33/ns-2.33/
NAM=/home/sadaq/ns-allinone-2.33/nam-1.13/
export PATH=$PATH:$XGRAPH:$NS:$NAM

thanks in advance
with regards
affu

---

