---
title: "Install VMware-Player-4.0.1 on UBUNTU 11.10 32Bit"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by mgualtie on 2011-12-06
Hello Everyone,
I have installed VMware-Player-4.0.1 using the file "VMware-Player-4.0.1-528992.i386.bundle".
The installation process was completed but, when I start the VMware the first time, a pop-up windows tell me about the Kernel headers 3.0.0-13-generic, in order to compile and load modules into the running kernel.
Seems that VMware client is unable to find the kernel headers automatically and asks for the correct path.

My Ubuntu uses the following Kernel:
mgualtieri@mgualtie-ThinkPad-T400:~$ uname -r
3.0.0-13-generic

The related Linux headers seems to be installed:
mgualtieri@mgualtie-ThinkPad-T400:~$ apt-cache search linux-headers-$(uname -r)
linux-headers-3.0.0-13-generic - Linux kernel headers for version 3.0.0 on x86/x86_64
linux-headers-3.0.0-13-generic-pae - Linux kernel headers for version 3.0.0 on x86

I have tried to pass the directory "/lib/modules/3.0.0-13-generic/build/include" but the following error message is returned:
"C header file matching your kernel were not found...."

Could you please help me?

Best regards
Massimiliano

---

### Post by T1Oracle on 2011-12-15
I get the same error on 64-bit, but I don't think VMWare supports 32-bit anymore.

---

### Post by lmihaila on 2012-01-21
you need to install some packages needed by the VMware Player installer: 
sudo apt-get install build-essential linux-headers-`uname -r`
thanks to Falko Timme on howtoforge.

---

### Post by raja.genupula on 2012-01-21
for more information look at this
[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

---

