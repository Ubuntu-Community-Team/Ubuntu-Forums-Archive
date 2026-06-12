---
title: "should i intall 32 or 64 bit"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by Matthew_Zepess on 2014-06-13
i got a hp/compaq presario c751nr. with 2gb of ram. should i install lubuntu 64 or 32. im new to linux and have been told this is a fast. lightweight distro. and good for beginners. i think its a 64bit compatible processor since i installed 64 bit vista without errors. and i think this is my processor [http://ark.intel.com/products/32432/Intel-Pentium-Processor-T2330-1M-Cache-1_60-GHz-533-MHz-FSB](http://ark.intel.com/products/32432/Intel-Pentium-Processor-T2330-1M-Cache-1_60-GHz-533-MHz-FSB) and it says 64 bit. is this the best choice, i was also thinking about linux ubuntu or mint

---

### Post by oldos2er on 2014-06-13
If you have a 64-bit processor, use 64-bit.

---

### Post by LastDino on 2014-06-13
Install Ubuntu or Xubuntu x64. 

Its always a good idea to install best possible architecture which supports the processor.

---

### Post by cecilieaux on 2014-06-16
OK, I ran lscpu in the terminal and got this output

> Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              6
CPU MHz:               2659.938
BogoMIPS:              5319.87
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K


Am I ready for 64-bit Ubuntu?

---

### Post by slickymaster on 2014-06-16
**lscpu** is telling you that your architecture is i686 (an Intel 32-bit CPU), and that your CPU supports both 32-bit and 64-bit operating modes. You won't be able to install x64 built applications since they're built specifically for x64 architectures.

---

### Post by LastDino on 2014-06-16
Your current OS is of x32. 

And yes, you can install x64 bit OS on that same machine since your processor supports it. And like slickymaster said, you will need x64 bit OS to support x64 built applications.

Here is how lscpu looks when running from x64 OS.
```

glen@maxwell:~$ lscpu
[B]Architecture:          x86_64
[/B]CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2003.000
BogoMIPS:              6000.18
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
NUMA node0 CPU(s):     0,1

```
Note the bold part.

---

