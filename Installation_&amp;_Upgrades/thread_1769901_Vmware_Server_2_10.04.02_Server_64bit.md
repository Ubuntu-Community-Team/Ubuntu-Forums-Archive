---
title: "Vmware Server 2 10.04.02 Server 64bit"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by famulusmercury on 2011-05-28
I have followed instructions on several threads here and other places and keep running into issues when compiling vmnet: 

Trying to compile vmnet module to see if it works
Performing make in /data/temp/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to ‘int’ in declaration of ‘DEFINE_SEMAPHORE’
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to ‘int’ in declaration of ‘DEFINE_SEMAPHORE’
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function ‘VNetFilter_HandleUserCall’:
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: ‘filterIoctlSem’ undeclared (first use in this function)
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/data/temp/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(

Again, I am running 2.6.32-31-server 64bit kernel and using the raducotescu patch. I have also tried manually downloading and installing a few other patches flying around, but still no luck. Also, all of the files are located in the same directory and I have tried running as root. Thanks for your help.

---

### Post by famulusmercury on 2011-05-29
I looks like all of the patches I have found are for different (newer, desktop mainly) kernels. I ended up just installing a bare-bones Debian configuration on the box. It takes up less than 400MB! Then I followed [_**this post **_]("http://www.troublenow.org/316/installing-vmware-server-2-0-2-on-debian-6-0-1-x64/") on how to install VMware Server on Debian. Installed everything without a hitch in about an hour.

---

