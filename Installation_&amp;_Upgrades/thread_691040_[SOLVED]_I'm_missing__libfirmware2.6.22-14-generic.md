---
title: "[SOLVED] I'm missing  /lib/firmware/2.6.22-14-generic file"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2008-02-08
My kernel upgrade to 2.6.22-14-generic hasn't worked. Looking for ideas I starting with-
"sudo apt-get remove linux-image-2.6.22-14-generic" 
I then updated 
Grub with " sudo update-grub"

Next
"sudo apt-get install linux-image-2.6.22-14-generic"
I noted the following lines

Suggested packages:
linux-doc-2.6.22 linux-source-2.6.22
The following NEW packages will be installed
linux-image-2.6.22-14-generic

update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory

When I look I've got the other kernels files even /lib/firmware/2.6.22-14-386 but I've got a dual core Athlon and need 2.6.22-14-generic to use both cpus.

Why isn't it there and how do I create the missing  /lib/firmware/2.6.22-14-generic file?
Does this missing file point to what went wrong with my kernel upgrade?
I'm not rebooted yet to see even if 386 works, I'd rather sort out generic.

---

### Post by Handssolow on 2008-02-08
This aspect of the problem I'm having upgrading my kernel to 2.6.22-14-generic has been resolved. Following advice on another thread from frodon, using Synaptic I installed two missing packages that probably had not been installed at the time of my attempted linux-header upgrade a few days ago,  they were-

Non free Linux 2.6.22 on x86/x86_64
Restricted Linux mudules for generic

I still not using 2.6.22-14-generic but at least I have the file /lib/firmware/2.6.22-14-generic.

---

