---
title: "Before install;  Download file selection"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by sceleratus on 2018-11-10
Hello,  I'm, like, way green.   I break out in a sweat when I see a command line.

I have a MinnowBoard (Intel Atom E3826) that I will use with pfSense.
I selected Ubuntu for the OS.

I started a download from what I thought was the correct directory only to notice the file name was "AMD"  Slammed on the brakes.
I did quite a bit of searching before posting here and there's not much Intel, or Atom, or E3826.

What do you suggest?
I'd be grateful if you'd point me in the right direction.

---

### Post by mitesh.agrwl on 2018-11-10
Hi,

In general CPU are two types - old ones prior to 2007-2008 based on architecture x86 with 32 bit instruction set and processors after 2007-2008 with 64 bit instruction set. 

Hence Linux uses following terminology based on architecture and instruction set. [More details]("https://help.ubuntu.com/community/SupportedArchitectures")

x86 for 32 bit (Introduced by Intel)
AMD or AMD_64 or x86_64 for 64 bit processors (Introduced by AMD).

Your processor is 64 bit (No matter Intel or AMD) you can use AMD files for it.

---

### Post by sceleratus on 2018-11-11
Gosh!!
My main-man MITesh

---

### Post by sceleratus on 2018-11-12
For a pfSense firewall do I want Desktop or Server code?
Also.....
Will a USB Bluetooth or 802.11 WiFi donegal boot up such that a  wireless keyboard and mouse work straightaway?   Almost all kbd are wireless.     I&#8217;ll check the docs too

thanks
Luke

---

### Post by mitesh.agrwl on 2018-11-12
Attention! The latest version of pfsense is not available as 'utility program'. They Have developed it as independent, ready to install, software based on FreeBSD, which can be installed directly on hardware. To use it no need to install base server/desktop. However if you have installed Ubuntu or want to use it with pfsense on same server will have to use Xen, which might complicate things with wireless keyboards and mouse.

However you can obtain the wireless card version/details using a live usb and check if it is supported by The FreeBSD or not. 

I am editing tags, so moderators can notice the thread and move it to proper support sub-forum.

---

