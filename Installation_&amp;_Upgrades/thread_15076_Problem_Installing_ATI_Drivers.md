---
title: "Problem Installing ATI Drivers"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by maaylix on 2005-02-11
I downloaded the .rpm pack from ati. Using root monitor, I converted the .rpm to .deb (sudo alien)

Then when i tryed to install (sudo dpkg -i fglrx-4-3-0_8.8.25-2_i386.deb), this is what came up: (I had to translate, because my ubuntu is in portuguese)

> Selecting packet previously not selected fglrx-4-3-0.
(Reading data bank ... 61307 files & directories instaled.)
Decompacting fglrx-4-3-0 (de fglrx-4-3-0_8.8.25-2_i386.deb) ...
dpkg: error processing fglrx-4-3-0_8.8.25-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in packet 
xlibmesa-gl
dpkg-deb: subprocess paste died by signal (Pipe broken)
Errors where found during processing of:
 fglrx-4-3-0_8.8.25-2_i386.deb

This graphic driver is for my Radeon 9600 Pro, I downloaded the XFree86 4.3 version

Also ATI mentions in it's HOWTO guide that the folowing are needed to install the driver:



        [LEFT]* glibc version 2.2 or 2.3
        * XFree86 version 4.1, 4.2, 4.3, or X.Org 6.8
        * Kernel source code
        * Kernel header (include) files
        * GCC compiler
        * Make Utility[/LEFT]

I just instaled Ubuntu and did the web update at install, I didn't install anything else sisnce then, am I missing one of these?

---

