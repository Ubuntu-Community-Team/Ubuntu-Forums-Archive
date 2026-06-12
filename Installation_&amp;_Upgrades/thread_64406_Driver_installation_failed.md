---
title: "Driver installation failed"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by nighttime on 2005-09-10
Ok, I don't think this is precisely the kind of installation this forum is about, but there's no specification as to installation of what heh so here it goes :P

My screen is stuck in an annoying 640x480 resolution, so I consulted some threats and apparently it's some driver problem, so I went looking for the right graphics driver for my 82865g intel card and I found it =D! BUT the installation fails to compile some modules... here's the error messages I got:

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

So I consulted dri.log and it contained...

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/oscarmier/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.

so is there some way I can summon /lib/modules/2.6.10-5-386/build into being? or something that'll make the darn thing work?

---

