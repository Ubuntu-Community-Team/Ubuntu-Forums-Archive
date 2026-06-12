---
title: "using GL and compiz"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by akashiraffee on 2009-12-18
I rebuilt the kernel using the 2.6.31 source package from ubuntu because my sound did not work with the generic kernel.

I am working on some openGL programming and now I get "cannot create direct rendering infrastructure on display 0:0" when I try to run anything. This appears to be rectified if I turn compiz off with "metacity --replace", but that mangles the desktop so badly I don't really see it as viable.

Using the default generic kernel, this does not happen -- but then of course I have no sound.  There are also other reasons I prefer a custom kernel, so the generic one is not an option, but this at least demonstrates that it is not a hardware limitation, and that compiz can run side by side with other GL applications.

Nb, I also have the kernel DRI module from my card installed, this did not make a difference.  The "cannot create" DRI does not happen all the time, but it usually does and once it does it will not stop.  And yes, I did build the fglrx module for both kernels seperately (I am using the latest ATI drivers, not the included ubuntu ones, altho I tried those too to the same effect).

Right now I have to go back to my old FC10 install to work on openGL.  Anyone know of a solution, or possible cause?  Also:  who should I file a bug with, compiz or ubuntu?

---

