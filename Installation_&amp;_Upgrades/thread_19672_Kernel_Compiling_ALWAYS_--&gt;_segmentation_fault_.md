---
title: "Kernel Compiling ALWAYS --&gt; segmentation fault !!!"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by MiddleBrooker on 2005-03-13
Hi,
First of all I would like to tell my satisfaction with this Ubuntu distro, because it's really a GREAT work!!

Now my problem is about a custom kernel that I would like to build with the appropriate source 2.6.10.
After :
```
make mrproper
make menuconfig
```

and after that
```

fakeroot make-kpkg clean
fakeroot make-kpkg buildpackage --revision=1.0.CustomKernel --appen-to-version=.130305 kernel_image --initrd binary
```  

I get ALWAYS the same error but ALWAYS related to different modules, randomically the segmentation fault happen in a different modules:

```

drivers/video/aty/radeon_base.c: In function `radeon_probe_pll_params':
drivers/video/aty/radeon_base.c:591: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[5]: *** [drivers/video/aty/radeon_base.o] Error 1
make[4]: *** [drivers/video/aty] Error 2
make[3]: *** [drivers/video] Error 2
make[2]: *** [drivers] Error 2
make[2]: Leaving directory `/usr/src/kernel-source-2.6.10'
make[1]: *** [stamp-build] Error 2
make[1]: Leaving directory `/usr/src/kernel-source-2.6.10'
make: *** [stamp-buildpackage] Error 2

```  


My hardware is:

Abit NF7-S with 2x512Mb Kingston HyperX and Hercules Radeon 9800PRO .

I'm trying to compile my custom kernel with the kernel 2.6.10-4-k7 but I've tryed with the kernel 2.6.8.1-5-k7 and the kernel 2.6.10-4-386 too.

Please can somebody tell me the problem ?

Thanks for all the support!!!
Best Regards,

MiddleBrooker

---

### Post by alastair on 2005-03-13
Odd - what version of GCC?

gcc -v

---

### Post by MiddleBrooker on 2005-03-13
Thanks for the reply, my gcc version is :

```
Reading specs from /usr/lib/gcc-lib/i486-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc i486-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
```


Many Thanks!!!

---

### Post by GilGalad on 2005-03-13
That might indicate some problem with the RAM modules. The fact that it does not break always in the same place also suggests that. You could run memtest and see if there are any errors.

---

### Post by MiddleBrooker on 2005-03-13
[QUOTE=GilGalad]That might indicate some problem with the RAM modules. The fact that it does not break always in the same place also suggests that. You could run memtest and see if there are any errors.[/QUOTE]

Yeah this is the problem, first of all after a recently memory upgrade on my system I've made an arror on the memory installation, because my NF7-S was not be able to run on dual channel, but anyway the're some compatibility problem with my board and HyperX memory  :-({|= 
But now after the dual channel mode seems to compile good :)

I hope that my new system that I've ordered through a website come to me soon!!
I've bought an Athlon 64bit and a Shuttle barebone...I hope to sole this stressfull problem.

Thanks for all the support!!

MiddleBrooker

---

