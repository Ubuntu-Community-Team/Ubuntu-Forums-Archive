---
title: "Install on 64bit CPU under ESXi 4 - Error"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by tu69 on 2010-06-04
Hey guys,

I am new here :) I tried to install Ubuntu Server 10.04 AMD64 onto my Dell blade server running ESXi 4. I get the following error when i try to install:

```
This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.

```.

My server have 2 Intel Xeon Quad core CPU's installed.
I have allocated 2 virtual CPU's to the VM. My VM is also set to Linux 64bit.

Any help would be appreciated.
Thank you in advance

---

### Post by oldos2er on 2010-06-04
I don't believe running 64-bit in a virtual machine will work. Try 32-bit.

---

### Post by davidmohammed on 2010-06-04
I think the error refers to you needing intel 64bit server not the amd64 edition.

---

