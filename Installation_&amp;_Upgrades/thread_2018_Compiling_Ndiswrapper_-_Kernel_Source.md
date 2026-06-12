---
title: "Compiling Ndiswrapper - Kernel Source?"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by chumpchous on 2004-10-25
I'm new to linux, and I'm trying to get my wireless internet working. I'm starting to figure things out, but I'm having a lot of trouble getting past one problem: running make install on ndiswrapper. I recieve the following error:

make [2]: Entering directory '/lib/modules/2.6.8.1-3-386/build'
make [2]: *** No rule to make target 'modules'. Stop.

I've googled around, and it appears I need to have my kernel source. I'm having a lot of trouble getting this done, mostly due to the fact that I'm not really sure what it means. I've tried apt-get install linux-image-2.6.8.1-3-386, but it doesnt change anything. 

Any advice? Thanks

---

### Post by Fabian on 2004-10-25
Hey,

maybe have a look here:

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

---

### Post by chumpchous on 2004-10-25
Yah, that would probably do the trick, but as far as I can tell, that particular system doesnt work without internet access, which I will not have until I get wireless working.

I've made a little bit of progress, (I think), with the manual installation, but now I come up with:
make [2]: Entering directory '/usr/src/linux-2.6.8.1'
Makefile:415: .config: No such file or directory
/usr/src/linux-2.6.8.1/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-2.6.8.1/scripts/gcc-version.sh: line 1: gcc: command not found
 CC [M] /usr/src/ndiswrapper-0.11/driver/wrapper.0
/bin/sh: line 1: gcc: command not found
make [3]: *** [/usr/src/ndiswrapper-0.11/driver/wrapper.0] Error 127
make [2]: *** [_module_/usr/src/ndiswrapper-0.11/driver] Error 2

I believe I have the source setup correctly. I have /libs/modules/2.6.8.1-3-386/build linked to my source directory in usr/src. The source is the linux-2.6.8.1.tar.bz2 that I downloaded off of kernel.org. 

So so far, no luck. Is there anyway to do this without a working internet connection?

---

### Post by chumpchous on 2004-10-25
I think I dont have the linux source configured properly. I downloaded linux-2.6.8.1 off of kernel.org an extracted it into my usr/src directory, but upon running /usr/src/ndiswrapper-0.11/debian/rules binary-modules KSRC=/usr/src/linux-2.6.8.1 it does a few things and then says the kernel source isnt available in that directory. Do I need to point it to a specific file? Do I not have the actual source? 

Thanks.

---

