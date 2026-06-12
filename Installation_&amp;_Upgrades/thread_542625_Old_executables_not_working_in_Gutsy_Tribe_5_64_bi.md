---
title: "Old executables not working in Gutsy Tribe 5 64 bits"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by oznelig on 2007-09-04
I have an old Suse 9.3 machine (32 bits) that works fine.
I also have a new core duo 3 GHz that has only given me grief so far.
After a terible struggle with DVD driver, network card and more, I
finally got Gutsy Tribe 5 64 bits to work.

The latest problem is that old executable compiled on the Suse machine
or precompiled by other people (i.,e. commercial app) that worked
fine there, no longer work.
Or rather, instead of getting a meaningful message, if I try to
execute one, I get a "no such file or directory" error.
Permissions are fine and the file IS there. I guess it's a way to say
that it can't be run.
My guess was that 32 bit executable were no good for 64 bits, but
this is not the case  :my friend has Fedora7 64 bits and all those
essential programs work fine. I could not install Fedora 7 as the DVD
was not recognized (a well known problem).
Any ideas ?

My friend suggests to install Fedora 7 with a USB driver. Last time I did it
stuffed up the winxp boot. So, I'm very reluctant to do that.

Thanks,

Enzo

---

### Post by oznelig on 2007-09-04
Solved : I needed to install the ia32-libs package.

Enzo

---

