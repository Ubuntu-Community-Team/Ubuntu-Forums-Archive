---
title: "Kernel source missing?"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by leaded on 2005-08-15
I have a dilemma. I'm installing Ubuntu on a new Dell Dimension 5100C. It's using a fairly new chipset, the Intel 945G, and I'm having some trouble. There's no updated video driver, but I'm okay using the Gerneric VESA driver for now. The bigger problem is that the Ethernet driver doesn't work. I solved this for a co-worker running the same hardware but running Fedora. Basically, I just need to update the Intel e100 network driver. I downloaded it from Intel's website and ran make but it needs to Kernel source (to create a kernel module). 

So, I can't do anything like apt-get install kernel-source because I don't have an Internet connection on the computer. I could download it and transfer it with a thumbdrive, but, where can I find it? It's the kernel source for the kernel that comes with 5.04 final.

Thanks.

---

### Post by jasmuz on 2005-08-15
Here is the URL for the kernel sources of the provided kernel in Ubuntu wich is 2.6.10-5:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/)

---

### Post by az on 2005-08-15
The build-essential and linux-heders-2.6.10-5-386 packages are on your cd.  That is all youneed to build a module.  You do not, in general, need the full source.

---

### Post by leaded on 2005-08-15
Shortly after I posted this, I searched Google for building modules. I found the package was called linux-headers and was able to install it from CD. I didn't need to do the build-essential though for the module I had to build. Thanks for the replies guys!

---

