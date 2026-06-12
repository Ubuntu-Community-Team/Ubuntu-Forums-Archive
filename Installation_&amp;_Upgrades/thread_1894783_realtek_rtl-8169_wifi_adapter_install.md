---
title: "realtek rtl-8169 wifi adapter install"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by Mikaelm on 2011-12-13
Hi,

Im new to linux and i need help

I have a wifi adapter (usb) for my ubuntu 11.10 server (pc)
but i dont know how to install drivers to have internet connection.

model number is Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev10)

I have a cd with drivers + usb stick with the drivers in (both connected) but i dont really know how to install them.

I have no internet connection because wifi is the only way.

I would really appreciate any help, thanks

---

### Post by Mark Phelps on 2011-12-13
You can't use the software and drivers that came with the adapter because they are for Windows, not for Linux.

Suggest that you browse the Networking forum to see if there are threads there dealing with your wifi adapter.

But, be advised, you will most probably have to download stuff to get the adapater working.

---

### Post by Mikaelm on 2011-12-13
I have the linux drivers in the cd and usb.

---

### Post by dandnsmith on 2011-12-14
If there aren't any (text) files suggesting how to use the linux driver files, then I suggest you post some info (eg a list) about what is there - after all, we cannot guess what you might have.

---

### Post by Mikaelm on 2011-12-14
[http://www.megaupload.com/?d=QZK5YRSI](http://www.megaupload.com/?d=QZK5YRSI)

You can download  it here and look into it.

There is one readme file, but i serously dont understand **** from it.

---

### Post by Mikaelm on 2011-12-14
Readme file says

1. Build up the drivers from the source code
	  make

	2. Install the driver to the kernel
          make install
          reboot

i dont know how to do first step, 
but when i do second step it tells me to install "make"
so i did apt-get install make and it sais package "make has no installation candidate..
this may mean that the package is missing, has been absoleted or is only available from another source.


anyone :) ?

---

### Post by dandnsmith on 2011-12-14
First check that /usr/bin/make exists on your system - if not, then it's probably some difference with the server package, rather than the desktop package. If it isn't there, then you may have to install kernel headers and some other source bits (forgotten which - last time I had to do this was, literally, decades ago) to get the assembly to work.

The instruction **make**, run in the same directory as the Makefile should do the first bit.

Next you need to do **make install**, as it says (same directory as Makefile) to install the module.

---

