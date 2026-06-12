---
title: "Kernel Recompile to suppot PAE OR x64 installation"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by chrisgibbs on 2008-03-30
Hi all,

I have recently installed 8Gb of memory into my main desktop for use as a GNS3 and vmware platform. Having only the standard 32bit OS installed I'm only able to see 3Gb of the memory. I would like to keep my current setup and still have the kernel support PAE if possible before considering the x64 platform as I have had issues previously with hardware and software suppot. If anyone has any thoughts or suggestions it would be greatly appreciated.

I have been following the guide as listed below but came unstuck when trying to compile the linux-restricted-modules. It appears that the versions don't align, when following the suggested methods. It may just be out of sync in the repository but I don't really want to waste 8hrs+ of compile time. I really need the nvidia modules and the vmware module otherwise it wouldn't really be a hassle. The new kernel works well apart from no gUI :)

Guide:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Kernel 
linux-image-2.6.22-9

Headers
linux-headers-2.6.22-9

Restricted Modules
linux-restricted-modules-2.6.22-14

I am currently running the following hardware:

1 x Intel Quad 2.4Ghz 
4 x 2Gb DDR2 667 Memory
1 x Nvidia 6800GTS 640Mb 

I am currently running the following software:

Ubuntu Gutsy (7.10)

---

