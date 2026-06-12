---
title: "howto get the nvidia kernel module built for a custom kernel"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by hanasaki on 2006-06-14
Built a new .deb kernel from a kernel.org download.  make-kpkg works like a champ.

**How do you build the nvidia kernel module for a custom kernel?**

---

### Post by Arnaud_B on 2006-06-14
you need the directory where you build it... usually I build it at the same time as the kernel with something like 
$make-kpkg --initrd --append-to-version=blabla kernel_image modules_image
so I guesss you could do (after unpacking the nvidia source of course...)
$make-kpkg modules_image simply :-)
or: $module-assistant a-i nvidia-kernel
or: $debian/rules binary_modules
in the last case you might want to set up KSRC and KVERS...
Good luck!
A.

---

### Post by Arnaud_B on 2006-06-14
Oh and just after doing that you install the nvidia deb you just did :-)
A.

---

### Post by hanasaki on 2006-06-15
m-a autoinstall nvidia reports the below error.
also... what is the .deb that should come out of the m-a?

make[2]: Entering directory `/usr/src/modules/nvidia-kernel/nv'           

NVIDIA: calling KBUILD...                                                 
make CC=gcc-4.0 -C /usr/src/kernel-headers-2.6.16.20 SUBDIRS=/usr/src/modu
make[3]: Entering directory `/usr/src/kernel-headers-2.6.16.20'           
/usr/src/kernel-headers-2.6.16.20/arch/i386/Makefile:38: /usr/src/kernel-h
make[3]: *** No rule to make target `/usr/src/kernel-headers-2.6.16.20/arc
make[3]: Leaving directory `/usr/src/kernel-headers-2.6.16.20'            
NVIDIA: left KBUILD.                                                      
nvidia.ko failed to build!                                                
make[2]: *** [mdl] Error 1                                                
make[2]: Leaving directory `/usr/src/modules/nvidia-kernel/nv'            
make[1]: *** [build-stamp] Error 2                                        
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel'          
make: *** [kdist_image] Error 2

---

### Post by Arnaud_B on 2006-06-15
the deb you should get is a nvidia-kernel-blabla blabla is the name of your kernel, like 2.6.15.7-ubuntu1 for instance... 
mmm.. but not sure to be able to help you for the error anyway check that:
- that the gcc version you used to build the kernel is the same as for the nvidia source
- that you have all the necessary stuff: kernel-package, libncurses5-dev, module-assistant, build-essential... (all are not essential depending on the way you build it...)
- that you have the original tree where you build your kernel (configured...)
- that you applied the ubuntu patches (btw you probably need dpatch and patchutils for that...)
well it's all I see... should work now...
Good luck,
A.

---

### Post by tseliot on 2006-06-15
1) Make sure you have the kernels headers for your kernel installed
2) If so, please try Method 2 of this guide of mine (it also clearly explains how to solve problems with the newest kernels):
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by hanasaki on 2006-06-15
followed your instructions and those at:
  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

getting the following error:
...
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function prefetch_range:
   include/linux/prefetch.h:62: warning: pointer of type void * used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:522,
                    from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function check_signature:
   include/asm/io.h:258: warning: wrong type argument to increment
   In file included from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/os-interface.c:26:
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv-linux.h:677:2:
   warning: #warning "conftest.sh failed, assuming remap_page_range(4)!"
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-interface.c: In
   function os_set_mlock_capability:
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-interface.c:137
   5: error: struct task_struct has no member named rlim
   make[3]: *** [/tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-i
   nterface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.

---

### Post by tseliot on 2006-06-15
[QUOTE=hanasaki]followed your instructions and those at:
  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

getting the following error:
...
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function prefetch_range:
   include/linux/prefetch.h:62: warning: pointer of type void * used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:522,
                    from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function check_signature:
   include/asm/io.h:258: warning: wrong type argument to increment
   In file included from /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv/os-interface.c:26:
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/nv-linux.h:677:2:
   warning: #warning "conftest.sh failed, assuming remap_page_range(4)!"
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-interface.c: In
   function os_set_mlock_capability:
   /tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-interface.c:137
   5: error: struct task_struct has no member named rlim
   make[3]: *** [/tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src/nv/os-i
   nterface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz5367/NVIDIA-Linux-x86-1.0-8178-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.[/QUOTE]
The explanation of Method 2 says:
> METHOD 2 If you need another driver version (e.g. the latest version if it is not available in the Ubuntu's repositories) or you have problems with Method 1 or you are using a kernel you have compiled yourself (thus lacking the restricted modules required for method one) or you want to try something different then Method 2 is for you. **[COLOR="Red"]This Method works ONLY with driver 8756 and 8762[/COLOR]**

Driver 8178 would require a patch. Please use 8756 or 8762

---

### Post by hanasaki on 2006-06-15
well I got the newest script fron nvidia.com and it ran fine.

question is... 1: how does one get the script (the specific one downloaded : not from the repository) to run under m-a what is the value of doing this vs just running the script as root.

---

### Post by tseliot on 2006-06-15
[QUOTE=hanasaki]well I got the newest script fron nvidia.com and it ran fine.

question is... 1: how does one get the script (the specific one downloaded : not from the repository) to run under m-a what is the value of doing this vs just running the script as root.[/QUOTE]
Module assistant uses the nvidia kernel source which is in the repos.

The installer has always the latest version.

---

