---
title: "Installing From .tar.bz2 and .tar.gz"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2006-06-13
Ok i have downloaded some things and i do not no how to install from .tar.bz2 and .tar.gz

ok first tar.bz2

i downloaded qtiplot and i extracted the files but i dont no what to do from there have a look at the screen shot

---

### Post by aysiu on 2006-06-13
These are the instructions from the README file: > For all the other  Linux  distributions and for  Mac OS X :
1) download the .tar.bz2 or the .zip archive and decompress it
2) open a terminal (console) window
3) go to the main folder of the decompressed archive
4) modify the 'qtiplot/qtiplot.pro' file in order to set the INCLUDEPATH and LIBS variables to point to the location of the zlib, GSL and QwtPlot3D libraries on your system (header files and dynamic lib files).
5) type "qmake"
6) type "make"
7) login as root and type "make install" I would assume you can get ahold of zlib, GSL, and QwtPlot3D?

---

### Post by CameronCalver on 2006-06-13
ok i am not sure what u meen can you download it and help me this is the conf file

TEMPLATE    =	subdirs

SUBDIRS = 3rdparty/qwt\

	  qtiplot-0.7.2

and also you no chmod can you tell me all the permission thing like 771 or 741 i cant remember  and what they do

---

### Post by CameronCalver on 2006-06-13
This is the file

---

