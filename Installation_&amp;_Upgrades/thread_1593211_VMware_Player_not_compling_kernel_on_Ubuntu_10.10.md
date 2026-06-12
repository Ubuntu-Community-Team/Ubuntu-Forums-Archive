---
title: "VMware Player not compling kernel on Ubuntu 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Barillo on 2010-10-11
Hi all,
I've just upgraded to Ubuntu 10.010 - Maverick Meerkat.

Launching VMWare Player 3.1.2 I get the message: "Before you can run VMWare, several modules must be compiled and loaded into running kernel".
I click ok, but there are problems recompiling VMCI sockets.
The effect is that my windows image starts, but then crashes.

Do you have some suggestions to solve the problem ? Or is it only a problem of compilation with the new 10.10 kernel, not yet available for VMWare ??
thanks

---

### Post by lechien73 on 2010-10-11
I had the same problem directly following the upgrade. The answer can be found here:

[http://blog.mattrudge.net/2010/10/11/vmware-player-on-ubuntu-10-10-maverick-meerkat/](http://blog.mattrudge.net/2010/10/11/vmware-player-on-ubuntu-10-10-maverick-meerkat/)

---

### Post by Barillo on 2010-10-11
thanks lechien73!

I followed your suggestions, and all the modules were recompiled.
Unfortunately the windows image is continuing to crash, into win32k.sys.
no ways to run my xp image....this was not happening before the migration, at 10.09 level.....
do you have some ideas ???

---

### Post by lechien73 on 2010-10-11
Are you starting up a saved snapshot? Or is this a fresh restart of the image?

I'm not sure why it would crash. I've tested all my images with the recompiled version and they're working fine. :confused:

---

### Post by imperialline on 2010-10-11
Works great! You are a genius! Thanks.

---

### Post by Barillo on 2010-10-12
yes, the crash is happening with a saved screenshot of the windows image.
I'm trying to start a new one to see if the problem is related to that saved specifical image.

thanks

---

### Post by PatrickD-52761 on 2010-10-22
Well this didn't work for me.  I'm getting an error on Line 189, and it's still failing to compile the VMCI.  However (at least before running the patches), I was able to open and use my VM's without any problems--other than the annoyance of having to try and fail compiling every time.

Hopefully VMWare will fix this issue pretty soon.  Although I'm going to guess nope, since it's their *free* version.  Any suggestions on fixing this are appreciated.

I should note that I'm on a 32-bit version of Ubuntu 10.10 2.6.35-22-generic kernel.

Have a great day:)
Patrick.

---

### Post by Objectivity on 2010-12-22
> **Barillo said:**
> Hi all,
I've just upgraded to Ubuntu 10.010 - Maverick Meerkat.

Launching VMWare Player 3.1.2 I get the message: "Before you can run VMWare, several modules must be compiled and loaded into running kernel".
I click ok, but there are problems recompiling VMCI sockets.
The effect is that my windows image starts, but then crashes.

Do you have some suggestions to solve the problem ? Or is it only a problem of compilation with the new 10.10 kernel, not yet available for VMWare ??
thanks


 This thread also was about this ... SOLVED for me .
[http://ubuntuforums.org/showthread.php?t=1650297](http://ubuntuforums.org/showthread.php?t=1650297)

---

