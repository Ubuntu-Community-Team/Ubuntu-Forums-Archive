---
title: "VMWare Tools GCC Path"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by kklingerman on 2005-06-29
Hi,

  You've probably heard this a million times, but I'm new to Linux and I've just installed Ubuntu 5.04 under VM-Ware 5.0.  I've tried to install the the VM tools, but I'm asked for a path to the GCC.  I've seen notes about running "which gcc" to find the path.  That doesn't seem to give me anything at all.  Any help in either providing the path or helping me find the path would be greatly appreciated.  

Thanks.

Kevin

---

### Post by The Na Kun on 2005-06-29
Well, did you install it?  
dpkg -l | grep gcc
if nothing is in there, and you didn't edit your repositories, then
sudo apt-get install build-essential
it will prompt for password and insert your cd. I think that gcc is in either /usr/bin/ or /usr/local/bin.. maybe /usr/sbin..

---

### Post by kklingerman on 2005-06-29
Ok,  Heres what I get from DPKG...

ii  gcc-3.3-base   3.3.5-8ubuntu2 The GNU Compiler Collection (base package)
ii  libgcc1        4.0-0pre6ubunt GCC support library

I looked in the places you specified and I see nothing labeled "GCC".  I'm trying not to be ignorant, but it seems to show no matter how hard I try.  So, my next question is down and dirty.  What I am I looking for and how do I relay that info.  It seems to be looking for a file name and path.  

Thanks again.

Kevin

---

### Post by The Na Kun on 2005-06-29
Okay, open search and type in gcc, make sure you are looking in filesystem, and hit find, then it will show you gcc.  I'm sure it's named gcc, if not that would be odd, but it probably is.  It might be under /usr/lib or /usr/local/lib.  In the odd chance that it has a different name (1 to 400 billion.. and this just gives name), less -a | grep *gcc* 
If nothing comes up with that, then gcc just.. isn't there. Will the command gcc even work?

---

### Post by kklingerman on 2005-06-30
OK, I see alot of files with gcc, but none just named gcc.  Here's what I got back from the search.  Which one should I use?  Thanks.

/var/lib/dpkg/info/libgcc1.shlibs
/var/lib/dpkg/info/libgcc1.list
/var/lib/dpkg/info/libgcc1.postinst
/var/lib/dpkg/info/libgcc1.postrm
/var/lib/dpkg/info/libgcc1.md5sums
/var/lib/dpkg/info/gcc-3.3-base.md5sums
/var/lib/dpkg/info/gcc-3.3-base.list
/var/cache/apt/archives/gcc-3.3_1%3a3.3.5-8ubuntu2_i386.deb
/var/cache/apt/archives/gcc_4%3a3.3.5-1_i386.deb
/usr/share/doc/libgcc1
/usr/share/doc/gcc-3.3-base
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz
/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/include/linux/compiler-gcc3.h
/usr/include/linux/compiler-gcc+.h
/usr/include/linux/compiler-gcc.h
/usr/include/linux/compiler-gcc2.h
/usr/lib/perl/5.8.4/linux/compiler-gcc+.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc3.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc2.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc.ph
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/gcc-lib
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libcomphelp3gcc3.so
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libsalhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libucbhelper2gcc3.so
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/X11R6/man/man1/gccmakedep.1x.gz
/usr/X11R6/bin/gccmakedep
/lib/libgcc_s.so.1

---

### Post by kklingerman on 2005-07-01
OK, I had to install the BUILD-ESSNETIAL and LINUX-HEADERS-2.6.10-5-386 packages and the VMWARE TOOLS installled just fine.  Thanks.

---

