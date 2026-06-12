---
title: "AMD Catalyst 13.12 on 12.04 failed because of missing kernerl headers"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by piecezzz on 2014-03-21
The installation failed when I ran dpkg -i *.deb and gave this error:

   dpkg: dependency problems prevent configuration of fglrx: 
  fglrx depends on linux-headers-generic | linux-headers-generic-lts-quantal | linux-headers; however: 
 **  Package linux-headers-generic is not installed. **
**  Package linux-headers-generic-lts-quantal is not installed. **
[B]  Package linux-headers is not installed. 

[/B] I've done this before, but I just can't figure it out now. 
I tried sudo apt-get install linux-headers-$(uname -r) and it says the newest is already installed.
Please help! :D

**EDIT** ran apt-get -f install for the headers, but it gave an error. I'm not sure if it failed, this is what it said

Error! Bad return status for module build on kernel: 3.11.0-18-generic (x86_64)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.

Here's the make.log
[B][SIZE=1]DKMS make.log for fglrx-13.251 for kernel 3.11.0-18-generic (x86_64)
Sat Mar 22 00:46:57 CET 2014
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS=/var/lib/dkms/fglrx/13.251/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
  CC [M]  /var/lib/dkms/fglrx/13.251/build/2.6.x/firegl_public.o
  CC [M]  /var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.o
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c: In function &#8216;KCL_ACPI_ParseTable&#8217;:
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: warning: passing argument 1 of &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217; makes integer from pointer without a cast [enabled by default]
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: note: expected &#8216;u32&#8217; but argument is of type &#8216;struct acpi_table_header *&#8217;
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217;
make[2]: *** [/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/13.251/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make: *** [kmod_build] Error 2
build failed with return value 2[/SIZE][/B]

---

### Post by sen_2008 on 2014-04-10
I'm having the same problem as you, I can't find any help for it online either.

---

### Post by su:bhatta on 2014-04-10
A little more information please:
Did you  have any Fglrx drivers installed , and did you purge them before trying to install the new one?
Did you get Fglrx 3.12 from AMD website ? 

Generally different Fglrx versions have incompatibility with  Xorg server versions.
so, it is best to use the Fglrx version that is available in the Ubuntu Repos.

Have a look here to see if following the steps helps:: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Edit: It seems like you have 13.251 version installed , you need to purge that first  and reboot.

---

