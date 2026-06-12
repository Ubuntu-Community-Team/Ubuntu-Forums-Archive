---
title: "Installing kernel and module sources"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by coquinho61 on 2007-10-09
Hi,

I am trying to build the latest snapshot of the pwc driver for my Philps SPC 900 NC camera. When running make, I get the error that 

/lib/modules/2.6.20.3-ubuntu1/build: No such file or directory. Stop.

I.e. I need the kernel module source. Searched the package manager, no development section. Tried 

apt-get install linux-source

and 

apt-get source linux-image-2.6.20-16-generic
apt-get build-dep linux-image-2.6.20-16-generic

as per the 'Kernel/compile' section of the ubuntu support pages. No effect. Can anyone help me out? 

Thanks,

Coquinho

---

### Post by rozen on 2007-10-13
I am also trying to rebuild the kernel, It seems that the stock desktop kernel does not support 4 GB of storage.

I know that this is no help to you, but where did you find 'Kernel/compile' section of the ubuntu support pages. I too need all the help that I can find.  I would like some insight on how to configure the kernel. Would you post an URL?

What I have done so far was to do the apt-get on the linux-source-2.6.20, move it to my home directory, unpack it, invoke make menuconfig where I changed the memory size thingie from 4GB to 64GB and finally 'make'. After about two hours, the make completed without any error messages.  But since I don't understand config, I am not sure what I have.  Will try testing it today.

Good Luck and Thanks in Advance,
Don

---

