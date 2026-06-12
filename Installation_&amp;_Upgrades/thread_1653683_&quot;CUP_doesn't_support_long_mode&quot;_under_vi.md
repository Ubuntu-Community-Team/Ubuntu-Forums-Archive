---
title: "&quot;CUP doesn't support long mode&quot; under virtualbox"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by h9uest on 2010-12-27
Hi:

I'm using Ubuntu 10.04, 64 bit. I've also verified through /proc/cpuinfo that I have two cpus that support long mode.

However, when I try to run virtualbox 3.1.6 and install FreeBSD as a virtual machine on my ubuntu host, I constantly get the error "CPU doesn't support long mode". The FreeBSD iso file is 64 bit. And I have already turned on virtualization support and VT-d through BIOS. I've restarted the system, and I still constantly get this same error.

How is that even possible?
I'm looking forward to hearing from you about suggestions and solutions.

Thank you.

---

### Post by DAE51D on 2011-10-04
Did you ever get a reply to this? I have something similar happening.
 
I run Windows7 32-bit on a Dell E6500 with P8600 CPU (dual core). 
 
VT is enabled in the BIOS.
 
I have a FreeBSD 8 64-bit Guest VM that I use at work, but whenever I try to boot it on my Dell notebook, it says "CPU doesn't support long mode". :confused:

---

