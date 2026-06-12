---
title: "error: kernel- sources cannot be found!"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by podrik0 on 2005-06-26
Next problem
error: kernel- sources cannot be found!
This happens at the end of ./configure

So effects the make which doesn't work properly I think

Anyideas? I think somehting like Kernel sources are missing I not sure? I no nothing about it lol

Thanks

---

### Post by irusun on 2005-06-26
More people might be able to help you if you explain what it is you're trying to do...

---

### Post by podrik0 on 2005-06-26
Sure
Installing my modem driver right now trying all day to get it working as I have not one bit of experience with linux!

3. Prepare the eagle-usb-driver
Download: eagle-usb-1.9.8.tar.bz2 from SourceForge download area (you may take latest version and adapt)
Unpack it somewhere: e.g. into /opt
cd /opt
tar xvfj eagle-usb-1.9.8.tar.bz2
cd /opt/eagle-usb-1.9.8
If no configure-file exists run
./autogen.sh
Then a configure-file should exist. Run
./configure --prefix=/usr

I'm on that section and have just ran ./configure and got that error, so I need do get the Kernel Source or something?

I have no internet connection on linux at the moment so am trying all I can do get it

Thanks

---

### Post by The Na Kun on 2005-06-26
[QUOTE=podrik0]Sure
Installing my modem driver right now trying all day to get it working as I have not one bit of experience with linux!

3. Prepare the eagle-usb-driver
Download: eagle-usb-1.9.8.tar.bz2 from SourceForge download area (you may take latest version and adapt)
Unpack it somewhere: e.g. into /opt
cd /opt
tar xvfj eagle-usb-1.9.8.tar.bz2
cd /opt/eagle-usb-1.9.8
If no configure-file exists run
./autogen.sh
Then a configure-file should exist. Run
./configure --prefix=/usr

I'm on that section and have just ran ./configure and got that error, so I need do get the Kernel Source or something?

I have no internet connection on linux at the moment so am trying all I can do get it

Thanks[/QUOTE]
 You need to install the kernel headers, so if you didn't edit your resp.s, then find the kernel headers and install them from the cd.

---

### Post by podrik0 on 2005-06-26
Hi,
Can you tell me how please  O:) ?

---

### Post by The Na Kun on 2005-06-26
Alright, open synaptic package manager from system > administration and click search and click not installed, then go and find the kernel headers there and check them and click apply, then insert your cd in and it will download them.

EDIT:  They are usually put in /usr/src/kernel-version so you might have to edit the script if it doesn't have that.

---

### Post by podrik0 on 2005-06-26
THANK YOU & everyone else who helped!! 
Finally online posting off linux my first!  :)

---

### Post by az on 2005-06-26
Great!

Just to note that in ubuntu, the packages are called "linux-headers"  For example:  linux-headers-2.6.10-5-386

---

