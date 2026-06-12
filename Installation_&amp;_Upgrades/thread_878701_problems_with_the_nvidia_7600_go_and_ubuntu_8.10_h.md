---
title: "problems with the nvidia 7600 go and ubuntu 8.10 how i have to fix it??"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Gabrix on 2008-08-03
hi at everyone in that site guys!
i am an italian user so sorry for my bad english if it come to uncomprensive ok?
so..
i have installed on my hp dv9084 ea my so beautiful ubuntu 7.10, after nights without sleep i finally got solutions to my  problems but when i do the upgrade to 8.10 it crash to all... sigh
i have tryed to patch the nvidia drivers 173.14.09 (the last?) but the sistem not recognize the x server settings of nvidia it says:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

i tryed the possible to my capacity  how i can do this?? 
i think that formatting and reinstalling is the solutions but how?!?!?!
if i want to reformat the partitions norton partition magic send methet are errors in process 
help me please and sorry for my log post

---

### Post by Pumalite on 2008-08-03
Download the driver from Nvidia and install it through a Virtual Terminal (Ctrl+Alt+F1)

---

### Post by Gabrix on 2008-08-03
yes i do it but it take to me error because i have the gcc4.3 and not the 4.2!
so i patch the NVIDIA-Linux-x86-173.14.09-pkg.run with a pathc taken in this forum, the xen.patch.txt, but nothing to do....
how i can do it?? please help me!!

---

### Post by Pumalite on 2008-08-03
Try:
sudo apt-get install linux-headers-`uname -r`

---

### Post by Gabrix on 2008-08-03
i do it and it take to me this:

linux-headers-2.6.24-20-generic is already at last version
linux-headers-2.6.24-20-generic set for manual installation
0 updated, 0 installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2008-08-03
I imagine you already installed the latest build-essential
Tell me the steps you take in the Virtual Terminal

---

### Post by Gabrix on 2008-08-03
latest build-essential?
i do the system update and updating it take to me errors
if i want to return to 7.10 how i can do??
with partition magic i can't reformat partitions it take me errors and i have windows too into the hd.. inserting ubuntu dvd and entering on menu' it stay with lamping cursor at left top screen an doing nothing

---

### Post by Pumalite on 2008-08-03
sudo apt-get install build-essential

---

### Post by logos34 on 2008-08-03
> **Gabrix said:**
> 
if i want to return to 7.10 how i can do??
with partition magic i can't reformat partitions it take me errors and i have windows too into the hd.. 
 
you can't rollback...and I doubt the partitions themselves are the problem.

You might try the latest driver ('.12'):

[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

alt+ctrl+F1

sudo /etc/init.d/gdm stop

cd /path/to/NVIDIA-Linux-x86_64-173.14.12-pkg2.run

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run --kernel-source-path=/usr/src/
linux-headers-2.6.24-20-generic

If it installs, run 

sudo nvidia-xconfig

sudo apt-get install nvidia-settings

sudo reboot

If you can get to the desktop but the screen settings are off, run

sudo nvidia-settings

---

### Post by Gabrix on 2008-08-03
yes i do it take me the time to try thanks ;)

but my pc is at 64 bit?!? O.o'
is intel centrino duo!
is a 64 bit machine?!? 
the drivers that u refer to use is for 64 bit?? no??

---

### Post by logos34 on 2008-08-03
sorry, typo/wrong page:

x86:

[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

But on second glance your problem appears to be a gcc mismatch...What is the output of these two commands:

cat /proc/version

gcc -v

(the first tells what version was used to compile the kernel, the second what
you are cuurently using--you have to build the nvidia kernel interface using the same gcc version
as the first)

---

### Post by Gabrix on 2008-08-03
Linux version 2.6.24-20-generic (buildd@rothera) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jul 28 13:49:52 UTC 2008

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.1-8ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.1 (Ubuntu 4.3.1-8ubuntu1)

---

### Post by logos34 on 2008-08-03
Both are GCC 4 releases...since it's only a difference between the .2.3 and .3.1, you could try the 'ignore' option:

 sudo sh NVIDIA-Linux-x86-173.14.12-pkg2.run --kernel-source-path=/usr/src/
 linux-headers-2.6.24-20-generic [B]--no-cc-version-check

[/B]for more info see:

sh NVIDIA-Linux-x86-173.14.12-pkg2.run --advanced-options

&

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/chapter-08.html)

If none of that works, try the [automatic route (EnvyNG]("http://www.albertomilone.com/envyngfaq.html#A"))

---

