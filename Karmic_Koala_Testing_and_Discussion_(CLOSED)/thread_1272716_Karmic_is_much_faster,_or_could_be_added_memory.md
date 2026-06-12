---
title: "Karmic is much faster, or could be added memory?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-09-22
Hi

I now have a very fast and pretty stable Karmic AMD64 running. It is much quicker than Jaunty. It also co-incides with putting in another 2GB of memory to make Qcad flow better.

Anybody else experiencing that Karmic is flying much better than Jaunty?

---

### Post by zika on 2009-09-22
> **bwallum said:**
> anybody else experiencing that karmic is flying much better than jaunty?+1

---

### Post by LKjell on 2009-09-22
> **bwallum said:**
> Hi

I now have a very fast and pretty stable Karmic AMD64 running. It is much quicker than Jaunty. It also co-incides with putting in another 2GB of memory to make Qcad flow better.

Anybody else experiencing that Karmic is flying much better than Jaunty?

I can remember someone said that if the system use 300mb of memory on load and you have 1gb then you are wasting 700mb :)

---

### Post by puccaso on 2009-09-22
take the memory out and test it?

---

### Post by xens on 2009-09-22
pretty fast and reacting on my eeepc1000H, I think that the UXA switch from intel drivers has something to do with that.

---

### Post by kansasnoob on 2009-09-22
Downright snappy!

---

### Post by NCLI on 2009-09-22
Extremely fast!  :guitar:

---

### Post by ibuclaw on 2009-09-22
> **LKjell said:**
> I can remember someone said that if the system use 300mb of memory on load and you have 1gb then you are wasting 700mb :)

Actually, don't believe the System Monitor. :P

Linux has two types of memory. Allocated and Cached.

What you see in System Monitor is the **usage of all allocated memory.**

Type in a terminal:
```
free -m
```
And you'll get something like this:
```

             total       used       free     shared    buffers     cached
Mem:          3038       1214       1824          0        168        563
-/+ buffers/cache:        481       2556
Swap:         4502          0       4502

```
To sum it up what you see:
Total RAM: 3GBs
Total RAM Used: 1.2GBs
What is Cached: 720MBs more or less
Bringing the total that System Monitor sees to around 480MB


See the screenshot to see the corresponding info from System Monitor.

Regards
Iain

---

### Post by LKjell on 2009-09-22
Well some memory are shared so technically you are using 481mb in memory. 1214mb is the union, and 481mb is the union minus the intersect. Or maybe I am wrong. So what is the difference between allocated and cached memory?

---

### Post by ibuclaw on 2009-09-22
> **LKjell said:**
> Well some memory are shared so technically you are using 481mb in memory. 1214mb is the union, and 481mb is the union minus the intersect. Or maybe I am wrong. So what is the difference between allocated and cached memory?

As far as I am aware, the cached memory is there to improve performance.

ie: you load an application, it takes a while to load as everything is being loaded from hard disk into memory.
When you close and reopen that application it is quicker to load as most files needed for it to load are in cache (RAM).

So, the more RAM you have, the better performance boost you will get from it, as it gives ample opportunity for Linux to cache as much as it wants in memory.


Allocated memory is what the loaded application is directly using for storage of variables, etc:
To go into programming jargon:
```
int *i = malloc(sizeof(int));
*i = 13;

```
The program is using a pointer i that is using an allocated slot of data in memory, while the program is running, the allocated slot will stay in memory, unless deallocated, then it will be free for other applications to use.

If you've ever heard of memory leaks, it's when a program is allocating too much memory without deallocating it.

Regards
Iain

---

### Post by andrewabc on 2009-09-22
Get more RAM, install preload, and you'll see more of your ram being used, and apps should start faster as they are preloaded into ram on startup.

[Tue Sep 22 18:02:46 2009] readaheading 1826 files
[Tue Sep 22 18:03:07 2009] 1122270kb available for preloading, using 1121156kb of it
I have 3 gb RAM. 
preload using 1.12 gb (loading 1826 files at startup!)
ubuntu reporting 650 mb used.
1.047 gb cached.

---

### Post by kansasnoob on 2009-09-22
Thanks Tinivole!

One of the things I love the most about Ubuntu is that I never stop learning :)

---

### Post by LKjell on 2009-09-22
> **tinivole said:**
> As far as I am aware, the cached memory is there to improve performance.

ie: you load an application, it takes a while to load as everything is being loaded from hard disk into memory.
When you close and reopen that application it is quicker to load as most files needed for it to load are in cache (RAM).

So, the more RAM you have, the better performance boost you will get from it, as it gives ample opportunity for Linux to cache as much as it wants in memory.


Allocated memory is what the loaded application is directly using for storage of variables, etc:
To go into programming jargon:
```
int *i = malloc(sizeof(int));
*i = 13;

```
The program is using a pointer i that is using an allocated slot of data in memory, while the program is running, the allocated slot will stay in memory, unless deallocated, then it will be free for other applications to use.

If you've ever heard of memory leaks, it's when a program is allocating too much memory without deallocating it.

Regards
Iain

What does it cache? And how does the program access the cache without compromising security? Assume a program cache some data and then terminate. Then another program tries to fool the system and access the cache?

---

### Post by ibuclaw on 2009-09-22
> **LKjell said:**
> What does it cache? And how does the program access the cache without compromising security? Assume a program cache some data and then terminate. Then another program tries to fool the system and access the cache?

I don't know that much, but I'm pretty sure it is protected from seldom attacks, and it's not just program access, it's also file access too (ie: if you grep some data across 20,000 files, the first time will be slow, then run the same action again and it should be slightly quicker than the previous time).

Just think of it as a way to speed up application delivery for disk-oriented applications (as apposed to cpu-oriented number crunching applications which only work better when there are more cores to produce threads with). Rather than always loading the same thing from disk, which is horribly slow in comparison.

As a quick example, here is the "command-not-found" application working away. Which in this example is a perl program checking about 5-6 databases for the existence of the key "gdc" until it is found. (In Ubuntu, this is actually a python application, but I found it to be [too slow]("http://ubuntuforums.org/showthread.php?t=1132464") :)).
```

jstdio@jstdio:~$ time gdc
The program 'gdc' can be found in the following packages:
 * gdc-4.1
 * gdc
Try: sudo apt-get install <selected package>

real	0m0.093s
user	0m0.020s
sys	0m0.020s
jstdio@jstdio:~$ time gdc
The program 'gdc' can be found in the following packages:
 * gdc-4.1
 * gdc
Try: sudo apt-get install <selected package>

real	0m0.025s
user	0m0.020s
sys	0m0.008s
jstdio@jstdio:~/Desktop$

```
Notice that the second run is almost 4 times quicker in comparison?

Regards
Iain

---

### Post by bwallum on 2009-09-23
> **kansasnoob said:**
> thanks tinivole!

One of the things i love the most about ubuntu is that i never stop learning :)+1

---

