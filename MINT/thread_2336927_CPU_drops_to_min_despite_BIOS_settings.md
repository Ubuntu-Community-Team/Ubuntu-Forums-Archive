---
title: "CPU drops to min despite BIOS settings"
date: 2016-09-12
forum: MINT
---

### Post by mechphisto2 on 2016-09-12
This is probably more a general hardware question, but not sure where else to ask.
I have:
Linux Mint 18 (Sarah) 64bit (Linux 4.4.0-36-generic)
```
$ cat /proc/cpuinfo | grep 'model name' | uniq
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
```

and it used to say 1.60GHz there, until I went into BIOS and changed the multiplier from auto to 9. 
As soon as I next logged in, I checked:
```
$ lscpu | grep MHz
CPU MHz:               2400.000
CPU max MHz:           2400.0000
CPU min MHz:           1600.0000
```

But after a few minutes, I noticed conky started showing 1.6. So I checked again:

```
$ lscpu | grep -i mhz
CPU MHz:               1600.000
CPU max MHz:           2400.0000
CPU min MHz:           1600.0000
```

My "System Profiler and Benchmark" (hardinfo) started out listing the cores at 2.4, then only the first core, now they're all 1.6.

What, why? If I turned the multiplier in BIOS to a set number instead of relying of speedstep (I presume), shouldn't it stay there?
I know it's working at least at first, but then, why drop again (as if speedstep is still working)?
There's nothing in the BIOS that actually mentions speedstep or anything like that, so I'm guessing the original "auto" setting was it.

Thanks for any suggestions!

---

### Post by DuckHook on 2016-09-12
*Thread moved to **The Cafe** as the more appropriate forum.*

This is not really an Ubuntu support question, so I've moved it here.

Have you tried the Mint forums? Mint may have configured their kernel to behave in a certain way. You might also try the forum (or help desk) of your MOBO manufacturer.

---

