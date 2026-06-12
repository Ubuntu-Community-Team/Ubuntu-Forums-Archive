---
title: "ffmpeg errors with libfaad.so.0"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-09-29
Ran into a problem:
$ ffmpeg
ffmpeg: error while loading shared libraries: libfaad.so.0: cannot open shared object file: No such file or directory

Diagnosis:
This is due to a library provided by faad2 package.  Karmic provides version 2.6.1 which is actually quite old.  If you have installed faad 2.7.X, then you will experience this problem.

Solution (stable but with old version):
Start synaptic, search for package faad2, force version 2.6.1 and everything works. 

Solution (new but untested):
Add fresh media ppa ([https://launchpad.net/~freshmedia/+archive/ppa](https://launchpad.net/~freshmedia/+archive/ppa)) and install new versions of ffmpeg, faad2 and vlc.

---

