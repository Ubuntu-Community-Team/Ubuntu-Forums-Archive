---
title: "how to install TOSSIM simulator"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by ribidi on 2012-02-26
Hi,
im a bigenner on Ubuntu 10.04 Lucid and i got a lot of problems when installing TOSSIM simulator. the links i fallowed are here :
[http://www.developerstation.org/2010...buntu-104.html](http://www.developerstation.org/2010...buntu-104.html) 
and
[http://pjpramod.blogspot.com/2009/01...-intrepid.html](http://pjpramod.blogspot.com/2009/01...-intrepid.html)



when i tape on the shell's prompt : make micaz sim 

hamza@hamza-laptop:/opt/tinyos-2.1.1/apps/Blink$ make micaz sim
mkdir -p simbuild/micaz
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
placing object files in simbuild/micaz
writing XML schema to app.xml
compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4a1352L -DIDENT_UIDHASH=0xe49b00fdL -Wno-nesc-data-race BlinkAppC.nc -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
compiling Python support and C libraries into pytossim.o, tossim.o, and c-support.o
g++ -c -shared -fPIC -o simbuild/micaz/pytossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4a1352L -DIDENT_UIDHASH=0xe49b00fdL /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx -I/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim -DHAVE_CONFIG_H 
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:139:20: error: Python.h: Aucun fichier ou dossier de ce type
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2501:4: error: #error "This python version requires swig to be run with the '-classic' option"
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:744: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:799: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:820: error: expected initializer before ‘*’ token
In file included from /usr/include/c++/4.4/stdexcept:38,
from /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2520:
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make: *** [sim-exe] Erreur 1

please some help and thank you.
i'm sorry for my bad english

---

### Post by ribidi on 2012-02-27
:(:(:(:(

---

### Post by coldraven on 2012-02-27
Your links don't work :(

---

### Post by ribidi on 2012-02-27
[http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html](http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html)

and

[http://www.developerstation.org/2010/09/installing-tinyos-on-ubuntu-104.html](http://www.developerstation.org/2010/09/installing-tinyos-on-ubuntu-104.html)

thanks for reply

---

### Post by coldraven on 2012-02-27
Those instructions are for Ubuntu 8.04 and you are using 10.04.
> 1) add bellow repository to your [FONT=courier new]/etc/apt/sources.list[/FONT]. Though it is for hardy, it is working for intrepid also

Try again, changing 
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy main
to
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main

---

### Post by ribidi on 2012-03-01
> **coldraven said:**
> Those instructions are for Ubuntu 8.04 and you are using 10.04.


Try again, changing 
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy main
to
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main

i'va changed to ubuntu 9.10, this is the guide of installation : [http://docs.tinyos.net/tinywiki/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages](http://docs.tinyos.net/tinywiki/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages)


the some problem persists. please i need your help and thank you 

hamza@hamza-laptop:/opt/tinyos-2.1.1/apps/Blink$ make micaz sim
mkdir -p simbuild/micaz
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
  placing object files in simbuild/micaz
  writing XML schema to app.xml
  compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f5e9cL -DIDENT_UIDHASH=0x75fc7048L -Wno-nesc-data-race BlinkAppC.nc   -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
  compiling Python support and C libraries into pytossim.o, tossim.o, and c-support.o
g++ -c  -shared -fPIC -o simbuild/micaz/pytossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f5e9cL -DIDENT_UIDHASH=0x75fc7048L /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx -I/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim -DHAVE_CONFIG_H 
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:139:20: error: Python.h: Aucun fichier ou dossier de ce type
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2501:4: error: #error "This python version requires swig to be run with the '-classic' option"
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:744: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:799: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:820: error: expected initializer before ‘*’ token
In file included from /usr/include/c++/4.4/stdexcept:38,
                 from /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2520:
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make: *** [sim-exe] Erreur 1

---

### Post by ribidi on 2012-03-01
[LEFT]finally it works, thanks to this site  [http://translate.google.tn/translate?hl=fr&langpair=en|fr&u=http://ubuntuforums.org/showthread.php%3Ft%3D1545343](http://translate.google.tn/translate?hl=fr&langpair=en|fr&u=http://ubuntuforums.org/showthread.php%3Ft%3D1545343)

this is the result i must got like this  site says : [http://docs.tinyos.net/tinywiki/index.php/TOSSIM](http://docs.tinyos.net/tinywiki/index.php/TOSSIM)

hamza@hamza-laptop:/opt/tinyos-2.1.1/apps/Blink$ make micaz sim
mkdir -p simbuild/micaz
  placing object files in simbuild/micaz
  writing XML schema to app.xml
  compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f8285L -DIDENT_UIDHASH=0x9d75bc1aL -Wno-nesc-data-race BlinkAppC.nc   -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
  compiling Python support and C libraries into pytossim.o, tossim.o, and c-support.o
g++ -c  -shared -fPIC -o simbuild/micaz/pytossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f8285L -DIDENT_UIDHASH=0x9d75bc1aL /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx -I/usr/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim -DHAVE_CONFIG_H 
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx: In function ‘void SWIG_Python_AddErrorMsg(const char*)’:
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:880: warning: format not a string literal and no format arguments
g++ -c  -shared -fPIC -o simbuild/micaz/tossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f8285L -DIDENT_UIDHASH=0x9d75bc1aL /opt/tinyos-2.1.1/tos/lib/tossim/tossim.c -I/usr/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim
g++ -c  -shared -fPIC -o simbuild/micaz/c-support.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4f8285L -DIDENT_UIDHASH=0x9d75bc1aL /opt/tinyos-2.1.1/tos/lib/tossim/hashtable.c -I/usr/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim
  linking into shared object ./_TOSSIMmodule.so
g++ -shared -fPIC  simbuild/micaz/pytossim.o simbuild/micaz/sim.o simbuild/micaz/tossim.o simbuild/micaz/c-support.o -lstdc++  -o _TOSSIMmodule.so
  copying Python script interface TOSSIM.py from lib/tossim to local directory
 
*** Successfully built micaz TOSSIM library. 

[/LEFT]

---

