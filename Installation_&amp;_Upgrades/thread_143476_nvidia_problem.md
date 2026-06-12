---
title: "nvidia problem"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by meskalin on 2006-03-12
hello,

i have a older graphic card and want to install the driver version 4349, because i had under windows problems with newer versions. the v 81 killed my system.

so i tried to intall the driver: sudo sh NVIDIA-Linux-x86-1.0-4349.run

and i got this message:
 ERROR: Unable to find the kernel source tree for the currently running kernel. 

the kernel version is:
2.6.10-5-386

but i dont know where to find the right kernel source and HOW to install it, 
i searched on google for 5hours and didnt find anything useful 

i tried : sudo apt-get install linux-image-2.6.10-5-386 linux-headers-2.6.10-5-386
but it seemed not to work

pleeeaaase help,
thx

---

### Post by Xian on 2006-03-12
I find it odd that the headers package didn't result in a better outcome. Normally, that would be all that is required. If you need the kernel source you can always get it in Synaptic via the package name linux-source-2.6.10. It will be placed in the /usr/src directory. You will then need to untar it and make a symlink named 'linux' (/usr/src/linux) to the linux-source-2.6.10 directory.

---

