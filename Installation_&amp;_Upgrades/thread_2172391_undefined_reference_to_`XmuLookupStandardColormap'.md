---
title: "undefined reference to `XmuLookupStandardColormap' in Ubuntu 12.04.3 LTS"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by acorsi on 2013-09-04
Hello,

I have just installed Ubuntu 12.04.3 LTS on a 64-bit machine and I'm having some trouble to compile an application using openGL. I suppose it is due to the different location of the libraries with respect to previous Ubuntu versions but I cannot fix the problem.

I define LD_LIBRARY_PATH in the .bashrc
LD_LIBRARY_PATH=$ROOTSYS/lib:${CLHEP_BASE_DIR}/lib:/usr/lib:/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH

And link the following libraries in the GNUMakefile
LDFLAGS += -L/usr/lib/x86_64-linux-gnu -lXmu -lglut -lGL -lGLU -lXi -lXmu

And got the following error message:
/home/irfulx168/mnt/acorsi/geant4/geant4.9.3/lib/Linux-g++/libG4OpenGL.so: undefined reference to `XmuLookupStandardColormap'

Could you give me some hint?
Thanks in advance,
Anna

---

