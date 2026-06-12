---
title: "compiz is memory leaked"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biji on 2009-04-21
I think compiz is memory leaked, it takes 974MB of memory while firefox only 828MB after few hours. compiz started at 300MB and after a few hours it ever reached 1500MB.. make my laptop feel slower. :(

   PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
   20   0  974m  40m 3304 S    2  2.1   4:53.81 compiz.real      
   20   0  828m 266m  13m S    5 13.9  25:57.00 firefox   

is there any options in ccsm to workaround this?

---

### Post by wfp on 2009-04-21
Looks like your looking at your virtual memory vs the actual ram memory being used. Firefox is using 266Mb of ram, and compiz is using 40Mb of your ram. That looks about normal to me. Not sure about why your system is slowing down, how much actual ram do you have installed.

---

### Post by biji on 2009-04-21
i don't think so.. IMHO 40MB is resource memory which is static, and over time.. virtual memory is used and increased which makes my swap being used
my system is: 64bit dual core 2G RAM

---

### Post by regala on 2009-04-21
> **biji said:**
> i don't think so.. IMHO 40MB is resource memory which is static, and over time.. virtual memory is used and increased which makes my swap being used
my system is: 64bit dual core 2G RAM

no, rss is resident memory, the memory actually used by the process.
virtual memory is only the total size of the address space mapped to be used by the code, the data, the bss of the process (including all mappings of shared libraries)

If I sum up all the "virtual memory" used by all the process of my system, it would just explode all my memory+swap.

---

### Post by portis on 2009-04-21
Indeed, there's a serious memory leakage with UXA and compiz.
See the bug report:[https://bugs.launchpad.net/compiz/+bug/328232](https://bugs.launchpad.net/compiz/+bug/328232)
and also: [http://bugs.freedesktop.org/show_bug.cgi?id=20704](http://bugs.freedesktop.org/show_bug.cgi?id=20704)

It is not completely resolved in the upstream.

---

### Post by portis on 2009-04-21
If I enable compiz, my 2Gb RAM can be consumed in 3 or 4 hours and swap starts to work. /proc/dri/0/gem_objects shows un unbelievable number of objects and bytes. The numbers increase all the time, and never decrease.
For the moment, I just disabled compiz.

---

