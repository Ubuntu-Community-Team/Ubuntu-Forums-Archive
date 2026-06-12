---
title: "VMware and nVidia problems after dist-upgrade to Dapper Fligt5"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by fantan on 2006-03-27
Hi for All!

Last week I did a lot of upgrades, and at last I got on my computer Dapper Flight 5 version.
But, from that time my VMware Workstation v5.5.1 which worked fine before
ships the following error message, and don't want to start anymore:
"albert@ubuntu:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
albert@ubuntu:~$" 

Can anybody tell me what it is, and the most important, how to fight with this error, how to get my VMware Workstation to work again?

The other problem is, that after the above mentioned upgrade my nVidia driver doesn't want to work anymore. I had to switch to vesa mode to get my system work properly.
If I try to download the nvidia-glx package again, and install it, I get the following error messages (I beg your pardon for my bad English, I try to translate the error message):

"albert@ubuntu:~$ sudo apt-get install nvidia-glx
Read packages list... Ready
Build Dependency tree... Ready 
I can't install some packages. This means, that you asked an impossible situation, or if you use the unstable distribution, then the required packages aren't ready yet or were moved out from Incoming repository.

Since you asked just one operation, this means more than possible that the package can't install in ordinary way and you should send some bugreport.
The following error messages may help you to find out the problem:

The following package has unresolved dependency:
nvidia-glx: depends from: libglu1-mesa, but this package isn't choosed for installation, or                  libglu1
E: Broken packages
Again, till now I used both the nvidia-glx driver and the VMware Workstation without any problems. The above mentioned problems are present just after upgrade to Dapper Flight5.

Can anybody help me?

Fantan 
albert@ubuntu:~$

---

### Post by fantan on 2006-03-27
Sorry for this e-mail!

I wanted to write to the other Forum Topic, not here.

Fantan

---

