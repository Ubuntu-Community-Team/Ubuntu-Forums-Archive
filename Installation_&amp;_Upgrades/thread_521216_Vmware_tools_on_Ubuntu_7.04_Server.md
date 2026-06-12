---
title: "Vmware tools on Ubuntu 7.04 Server"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by marco.giordano on 2007-08-09
Hi,

I have Ubuntu 7.04 SERVER installed on a Vmware Server virtual machine.
Everything seems to be ok, except that I'd like to have Vmware tools installed for power synchronization with the host o.s.
I followed this [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools) (I installed build-essentials and linux-headers for server release too) but:

when vmware-config-tool.pl starts, it finds that "none of the pre-built vhgfs module for vmware tools is suitable for you running kernel..." and I answer to try to compile a new one.
Then it asks for the location of C header files and when I answer
"/usr/src/linux-headers-2.6.20-16-server/include" or even
"/usr/src/linux-headers-2.6.20-16/include" or even
"/usr/src/linux-headers-2.6.20-16-generic/include"
it founds that "the directory of kernel headers (version @@VERSION@@ UTS_RELEASE) does not match your running kernel (version 2.6.20-16-server). Even if the module were to compile successfully, it would not load into the running kernel." And then asks again for the location of C header files.

Consider that, as I've already written, I installed build-essentials, linux-headers-2.6.20-16, linux-headers-2.6.20-16-generic, linux-headers-2.6.20-16-server and even vmware-tools-kernel-modules-2.6.20-16, hoping they would have fit without recompiling, but nothing seems to work.

Some advice?

Thanks in advance.

Marco

---

