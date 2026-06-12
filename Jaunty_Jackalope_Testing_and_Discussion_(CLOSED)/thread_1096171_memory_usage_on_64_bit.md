---
title: "memory usage on 64 bit?"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-14
this is the first time i have run ubuntu 64 bit on any of my machines, but is it normal to be using like....a lot more ram?

On almost all of my comps that run ubuntu, while its not doing anything it uses around 250-300 mb of ram

here, im using around 500 mb, and it seems that every program in the process list is using several more MB of memory then i am used to seeing in 32 bit ubuntu...is this normal?

---

### Post by smbm on 2009-03-14
As far as I know it's normal for 64bit stuff to use more ram. 

There is a sticky in the 64bit forum that mentions it, I'll see if I can find a link.

EDIT

From:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

> One disadvantage of 64-bit architectures compared to 32-bit architectures is that the same data will occupy more space in memory (due to larger pointers and possibly other types and alignment adding).
Note: The increases in the memory requirements of a given process can have implications for efficient processor cache utilization.

---

### Post by Polygon on 2009-03-14
i've read that too...but should the difference be like 100's of MBs? like, when im running eclipse, java is using around 500 MB of ram! When i was running eclipse in arch linux on the same laptop, it used no where near that much. Like, its getting to the point where vista is using less ram running the same programs O.o

---

### Post by hyperdude111 on 2009-03-14
64bit will use more ram because instead of data pointers being the thin 32bits wide they are the fat 64bits wide.

The difference in RAM usage will vary.

---

### Post by Sockerdrickan on 2009-03-14
Don't use Java as an example.

---

### Post by smbm on 2009-03-14
> **Polygon said:**
> i've read that too...but should the difference be like 100's of MBs? like, when im running eclipse, java is using around 500 MB of ram! When i was running eclipse in arch linux on the same laptop, it used no where near that much. Like, its getting to the point where vista is using less ram running the same programs O.o

My memory usage went up by half when I changed from 32 to 64bit.

Under 32bit with all my usual apps open I was using about 600mb now I'm on 64bit it's more like 900mb.

---

### Post by Polygon on 2009-03-14
hmm. Well, i do have 2 gigs of memory, its just disconcerting that running firefox and eclipse means i use about half that now xD

thanks.

---

### Post by smbm on 2009-03-14
> **Polygon said:**
> hmm. Well, i do have 2 gigs of memory, its just disconcerting that running firefox and eclipse means i use about half that now xD

thanks.

I hear you on that, I have 2.5gb and am using just under a gig with firefox, pidgin, gnome-do, synaptic and a couple of terminals open.

---

### Post by jp_coll2003 on 2009-03-14
> **Polygon said:**
> this is the first time i have run ubuntu 64 bit on any of my machines, but is it normal to be using like....a lot more ram?

On almost all of my comps that run ubuntu, while its not doing anything it uses around 250-300 mb of ram

here, im using around 500 mb, and it seems that every program in the process list is using several more MB of memory then i am used to seeing in 32 bit ubuntu...is this normal?

I have only found that the Jaunty 64 bit uses a lot more memory. I have two gig of memory and in Hardy and Intrepid usually I used about 270 mb. Now in Jaunty, I am using over 450 + mb of memory. Quite worrying.

---

### Post by ktp on 2009-03-14
How is everyone checking memory usage?

---

### Post by jp_coll2003 on 2009-03-14
> **ktp said:**
> How is everyone checking memory usage?

top command

---

### Post by tad1073 on 2009-03-14
If you don't have more that 4gig's you realy don't need to use the 64 bit version unless your cpu is 64 bit

---

### Post by ronacc on 2009-03-14
you can't use the 64bit version if your cpu isn't 64bit.

---

### Post by smbm on 2009-03-14
> **tad1073 said:**
> If you don't have more that 4gig's you realy don't need to use the 64 bit version unless your cpu is 64 bit

Even if you don't have 4gbs of RAM there are still performance improvements with 64bit.

---

### Post by kayosiii on 2009-03-14
Eclipse is a bad example to use here -- Java will take a set amount of ram for itself away from the system. Eclipse can be configured to take a lot of ram or a little bit.... It performs a lot better If it takes a lot....

Does top shows the amount of cached ram?

Also what happened to the system/Application/Cached Ram display in KDE's performance monitor?

---

### Post by vancouverite on 2009-04-12
Hi all,
This is an interesting thread.  I posted a few days ago here

[http://ubuntuforums.org/showthread.php?t=1119467](http://ubuntuforums.org/showthread.php?t=1119467)

about my machine using **LOTS** of memory even when it was doing nothing! I posted the output of *free* which shows that I was using 1.4 GB of memory after cache was subtracted. Seems like too much.

I also posted the output of *ps aux* (which I mistakenly said was the output from *top*) and I couldn't get all the memory usage listed in *ps* to total the 1.4 GB.

I am running 64 bit, 8.10 and it may be significant that this occurred after Vuze had been running for a while. I notice high memory usage consistently when using Vuze now, but it doesn't free it up when I quit Vuze. I did not have this problem when I was using 32 bit, 8.04.

I may be reading the output of *free* wrong, but I think line 1 tells me that I'm using 1.9 GB of memory and that of that about 500 MB is (buffers + cache). Is that correct? It was suggested in the other thread that I was reading the output improperly.

I think that I will be switching back to 32 bit when 9.04 comes out...

Cheers,
Van

---

### Post by Polygon on 2009-04-12
oh btw, this is a ubuntu problem. I just tried arch on the same laptop, and its using the same amount of ram it was using when running 32 bit. So...i'm not sure what exactly is making ubuntu use 300+ extra mb of memory then when its running in 32 bit

---

