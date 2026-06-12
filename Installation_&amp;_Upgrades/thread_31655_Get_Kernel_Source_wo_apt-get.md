---
title: "Get Kernel Source w/o apt-get"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by adajar99 on 2005-05-04
hello,

i need to recompile the kernel to incorporate the driver for my winmodem.  first, i need to get the kernel source.  unfortunately, all the instructions i have seen refer to doing the apt-get/synaptic.  but because i have no modem installed in my linux box, i will have to get the sources using another computer running windows.

so how do i get the kernel sources using a windows machine?  how do i proceed to recompile the source once i have it in my ubuntu box?

thanks!

---

### Post by cutOff on 2005-05-04
You can download it from 

[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/) 

It's called linux-source-2.6.10_2.6.10-34_all.deb

To install it

$ sudo dpkg -i linux-source-2.6.10_2.6.10-34_all.deb

---

### Post by adajar99 on 2005-05-04
hello,

thank you very much!  it's these forums and helpful people that make switching to linux a breeze.

---

### Post by Zelut on 2005-05-09
do we have any instructions on how to recompile the kernel if downloaded from the above link?  I need to recompile mine in an attempt to get my wireless working.  I'd appreciate any help.

---

### Post by Xian on 2005-05-09
[QUOTE=kuyaedz]do we have any instructions on how to recompile the kernel if downloaded from the above link?[/QUOTE]
There's some information about this over at the Wiki: [Kernel Compile How-To](http://www.ubuntulinux.org/wiki/KernelCompileHowto/view?searchterm=kernel)

---

### Post by az on 2005-05-10
[QUOTE=kuyaedz]do we have any instructions on how to recompile the kernel if downloaded from the above link?  I need to recompile mine in an attempt to get my wireless working.  I'd appreciate any help.[/QUOTE]


Very often, you do not need to recompile your kernel.  All you need are the kernel headers.  You can find the packages named linux-headers.  The install cd contains the linux-headers for the stock kernel. 

You should be able to compile any driver for the running kernel using only your install cd.

install build-essential and linux-headers-2.6.10-5-386

---

