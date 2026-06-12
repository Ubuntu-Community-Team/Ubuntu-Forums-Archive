---
title: "unable to run VMD - 3D visualisation tool"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by balajinm on 2012-10-25
Hi all,

I tried to install VMD on my Ubuntu . Installation was successful. But , when I tried to visualize a ".xyz" file , i get following message from VMD . I am not sure what to do. But I require it desperately.

> rlwrap: Command not found.
Info) VMD for LINUXAMD64, version 1.9.1 (February 1, 2012)
Info) [http://www.ks.uiuc.edu/Research/vmd/](http://www.ks.uiuc.edu/Research/vmd/)                         
Info) Email questions and bug reports to [email]vmd@ks.uiuc.edu[/email]           
Info) Please include this reference in published work using VMD:   
Info)    Humphrey, W., Dalke, A. and Schulten, K., `VMD - Visual   
Info)    Molecular Dynamics', J. Molec. Graphics 1996, 14.1, 33-38.
Info) -------------------------------------------------------------
Info) Multithreading available, 4 CPUs detected.
Info) Free system memory: 3172MB (82%)
Warning) Detected a mismatch between CUDA runtime and GPU driver
Warning) Check to make sure that GPU drivers are up to date.
Info) No CUDA accelerator devices available.
Warning) Detected X11 'Composite' extension: if incorrect display occurs
Warning) try disabling this optional X server feature.
Xlib:  extension "GLX" missing on display ":0".
ERROR) The X server does not support the OpenGL GLX extension.   Exiting ...
Info) VMD for LINUXAMD64, version 1.9.1 (February 1, 2012)
Info) Unable to create OpenGL window.
balaji@balaji-Inspiron-N5110:~/Desktop/graphite$ 

---

### Post by iloveX on 2013-04-06
I am also having the same problem, but in a slightly different scenario. I just got hold of a 64-bit machine, and can run VMD on this machine locally. Also, I was able to run VMD on a remote cluster (log in by ssh), but now when i try to run VMD in the cluster, i get the same error message as the above. My machine runs on Ubuntu 12.10. The cluster runs on Red Hat Enterprise Linux Server release 5.4.

---

