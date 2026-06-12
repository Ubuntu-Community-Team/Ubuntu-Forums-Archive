---
title: "tar.tar?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ann pic on 2008-02-23
What command need to instal tar.tar file?I use command similar to tar.gz file.But it cannot.. The tar.tar file don't have configure file, make and make install file. Anyone can help me? I really need help. The output is as below.

ann@anndesktop:~$
tar *xvf
/home/ann/desktop/bttv0.9.15.
tar.tar
bttv0.9.15/
bttv0.9.15/
v4l1compat.
c
bttv0.9.15/
v4l2common.
c
bttv0.9.15/
videobuf.
c
bttv0.9.15/
videobuf.
h
bttv0.9.15/
videodev.h
bttv0.9.15/
videodev2.h
bttv0.9.15/
tuner.c
bttv0.9.15/
tuner.h
bttv0.9.15/
tda9887.c
bttv0.9.15/
tda9887.h
bttv0.9.15/
id.h
bttv0.9.15/
audiochip.h
bttv0.9.15/
i2ccompat.
h
bttv0.9.15/
doc/
bttv0.9.15/
doc/CVS/
bttv0.9.15/
doc/CVS/Root
bttv0.9.15/
doc/CVS/Repository
bttv0.9.15/
doc/CVS/Entries
bttv0.9.15/
doc/CARDLIST.bttv
bttv0.9.15/
doc/CARDLIST.saa7134
bttv0.9.15/
doc/CARDLIST.tuner
bttv0.9.15/
doc/Cards
bttv0.9.15/
doc/MAKEDEV
bttv0.9.15/
doc/README.bttv
bttv0.9.15/
doc/README.cx88
bttv0.9.15/
doc/README.ir
bttv0.9.15/
doc/README.saa7134
bttv0.9.15/
doc/SoundFAQ
bttv0.9.15/
doc/Tuners
bttv0.9.15/
doc/insmodoptions
bttv0.9.15/
doc/notincx2388xdatasheet.
txt
bttv0.9.15/
doc/README.cx88~
bttv0.9.15/
ircommon.
c
bttv0.9.15/
ircommon.
h
bttv0.9.15/
msp3400.c
bttv0.9.15/
msp3400.h
bttv0.9.15/
tvaudio.c
bttv0.9.15/
tvaudio.h
bttv0.9.15/
tvmixer.c
bttv0.9.15/
bt848.h
bttv0.9.15/
btcxrisc.
c
bttv0.9.15/
btcxrisc.
h
bttv0.9.15/
bttvcards.
c
bttv0.9.15/
bttvdriver.
c
bttv0.9.15/
bttvgpio.
c
bttv0.9.15/
bttvi2c.
c
bttv0.9.15/
bttvif.
c
bttv0.9.15/
bttvrisc.
c
bttv0.9.15/
bttvvbi.
c
bttv0.9.15/
bttv.h
bttv0.9.15/
bttvp.h
bttv0.9.15/
bt832.c
bttv0.9.15/
bt832.h
bttv0.9.15/
irkbdgpio.
c
bttv0.9.15/
irkbdi2c.
c
bttv0.9.15/
Makefile
bttv0.9.15/
Make.config
bttv0.9.15/
linux
bttv0.9.15/
media
bttv0.9.15/.
tmp_versions/
bttv0.9.15/.
tmp_versions/videobuf.
mod
bttv0.9.15/.
tmp_versions/v4l1compat.
mod
bttv0.9.15/.
tmp_versions/v4l2common.
mod
bttv0.9.15/.
tmp_versions/btcxrisc.
mod
bttv0.9.15/.
tmp_versions/ircommon.
mod
bttv0.9.15/.
tmp_versions/bttv.mod
bttv0.9.15/.
tmp_versions/tuner.mod
bttv0.9.15/.
tmp_versions/tda9887.mod
bttv0.9.15/.
tmp_versions/msp3400.mod
bttv0.9.15/.
tmp_versions/tvaudio.mod
bttv0.9.15/.
tmp_versions/tvmixer.mod
bttv0.9.15/.
tmp_versions/irkbdgpio.
mod
bttv0.9.15/.
tmp_versions/irkbdi2c.
mod
ann@anndesktop:~$
ln *s
bttv0.9.15
bttv
ann@anndesktop:~$
cd bttv
ann@anndesktop:~/
bttv$ ./configure
bash: ./configure: No such file or directory
ann@anndesktop:~/
bttv$
ann@anndesktop:~/
bttv$

---

### Post by toa on 2008-02-23
You mean what command extracts tar.gz files

usually you

->extract
->configure 
->make (sudo!)
->install  (sudo!)

---

### Post by zvacet on 2008-02-23
@ **ann pic**

One post for one question,please.Be patient and somebody will help you.

---

