---
title: "sensor module from scratch... HELP :("
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by keithjr on 2006-06-09
For the love of pete, somebody help me get this module to work.

<Optional Background Info>
Last week I decided, after a series of OS-rending overheats, that I wanted to get my temperature sensors to work.  Following the guide to doing so in Breezy (which I was in at the time) with lm-sensors, I wound up with an odd warning.  It said that I needed a module, vt1211, which was not installed.  

This simple request sent me on a maddening spiral of confusion which has consumed my linux-going experience for the past 5 days.  First, I had to find the source for this module myself.  Then, it turns out there's no version for the default breezy kernel (or any for 2.6.12 at all).  There's a thread which states that one exists but gives no details on getting it working or where to find it (broken link), so I gave up and decided to upgrade my kernel.  

Doing so seemed to ruin my fglrx setup, so after spending a day trying to reconfigure THAT, and finding there were no apt-gettable packages that could help me in that kernel, I tried upgrading to dapper.  This was fairly painless and now I sit in a shiny new, default 2.6.15 kernel.  
</Background>

Finally, the source, vt1211.c, will compile, and makes itself .o, .ko, .mod.o, and .mod.ko files.  Just when I think I'm in the clear, I issue insmod ./vt1211.o  and I get a bogus error that it is an unrecognized module format (I'm not at my comp right now, I'll edit this later and paste the actual output).  I tried the .ko file and insmod complains about unrecognized symbols.  I try modprobing the file in the current directory, it says not found.  I try coping all of the object files into /lib/modules/drivers/i2c/chips (where it's buddies wait) and modprobe still can't find it.  I tried putting it in /usr/src/mykernelversion/drivers/i2c/chips, still no joy.  What on earth do I have to do to get this compiled module to load into the kernel?  :confused: 

As I said, I'll edit this later when I get home...

Thanks in advance

---

### Post by keithjr on 2006-06-09
I'm sorry, I accidentally put this in the wrong subforum.  Somebody can move it if they wish.

Cheers.

---

