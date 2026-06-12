---
title: "matlab install help"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by scholzilla on 2008-08-21
My university offers free downloads of matlab, and there is a linux version but ubuntu is not one of the supported linux distros. The matlab folks say, though, that it can be installed on other linux distros. They add this caveat:

"For any other 32-bit or 64-bit Linux distribution not explicitly listed, R2008a requires the distribution to be built using Kernel 2.4.x or 2.6.x and glibc (glibc6) 2.3.4"

Is there anyone with the patience/experience to walk me through this? I don't think I've ever done a build and don't know where to start.

Thanks

---

### Post by ad_267 on 2008-08-21
There's this: [https://wiki.ubuntu.com/MATLAB](https://wiki.ubuntu.com/MATLAB)

That's pretty cool you get a free download. I still had to pay for the student edition from my Uni and got the windows version a while ago. Now I just use Octave which is an open source clone of Matlab if I have to write matlab code, or I use SciPy for anything that doesn't require matlab compatability.

If you're using 8.04, glibc is version 2.7 and the kernel is 2.6.24 so both of those should be fine.

---

### Post by linux_tech on 2008-08-21
You can download Ubuntu from here-   [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
I don't know your system specs. You will need to select correct cpu (amd, i386, etc.)
If you have at least 500MB RAM, then you can run live cd version of install.
After downloading, make your iso and install.  You can choose "guided" 
for partitioning.   After installing, go into synaptic package manager and search for glibc6, or if necessary you can download this and install.

Ubuntu Hardy Heron Installation Guides
[https://help.ubuntu.com/8.04/install...rpc/index.html](https://help.ubuntu.com/8.04/install...rpc/index.html)
[http://www.howtoforge.com/the-perfec...ts-hardy-heron](http://www.howtoforge.com/the-perfec...ts-hardy-heron)

Ubuntu User Guide
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

If you are setting up a dual boot, good install guides can be found here:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

