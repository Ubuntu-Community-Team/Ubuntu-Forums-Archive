---
title: "nvidia"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by sheylock on 2005-05-03
Hi *,

I am currently trying to install the NVIDIA-Linux-x86-1.0-6111-pkg1 drivers on my 5.04 system, since I only have an old GeForce 3 Ti200 card installed in my server and the standard drivers don't seem to work.

Anyhow, half way through the installation, when the installer starts compiling the new kernel module, I am greeted by the following error:

<<<<<<< SNIP <<<<<<<<
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely because the kernel module was built using the wrong kernel source files.  Please make sure you have installed the kernel source files for your kernel; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' rpm installed.  If you know the correct kernel source files are installed, you  may specify the kernel source path with the '--kernel-source-path' commandline option.
>>>>>>> SNAP >>>>>>>>

I am quite positive that I have the correct kernel sources installed, as those were the ones I used to rebuild the kernel and got rid of some RIVA module that was being loaded by default.

Any hints on what might be causing this?

Some info on the system:

sheylock@haven:/tmp$ uname -a
Linux haven 2.6.10050503 #1 Tue May 3 07:48:25 CEST 2005 i686 GNU/Linux

sheylock@haven:/tmp$ ls -l /usr/src/
total 99236
-rw-r--r--   1 root     src   6743034 2005-05-03 10:38 kernel-doc-2.6.10050503_10.00.Custom_all.deb
-rw-r--r--   1 root     src   5144734 2005-05-03 10:39 kernel-headers-2.6.10050503_10.00.Custom_i386.deb
-rw-r--r--   1 root     src  14747512 2005-05-03 09:29 kernel-image-2.6.10050503_10.00.Custom_i386.deb
-rw-r--r--   1 root     src  37402286 2005-05-03 09:39 kernel-source-2.6.10050503_10.00.Custom_all.deb
lrwxrwxrwx   1 sheylock src        19 2005-05-02 23:34 linux -> linux-source-2.6.10
drwxr-sr-x  20 sheylock src      4096 2005-05-03 10:39 linux-source-2.6.10
-rw-r--r--   1 root     root 37431992 2005-04-05 15:26 linux-source-2.6.10.tar.bz2
drwxr-xr-x   7 root     root     4096 2005-05-02 22:14 rpm

Any help is greatly appreciated!

-S

---

### Post by sheylock on 2005-05-03
errr... sorry to bother y'all.

Switched out the 6111 package for the 6629 one and voilà, no more errors during compilation of the module. 

Sorry.

-S

---

