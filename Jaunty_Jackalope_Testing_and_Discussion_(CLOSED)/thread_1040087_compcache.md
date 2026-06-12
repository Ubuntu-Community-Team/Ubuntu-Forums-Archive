---
title: "compcache?"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by AndersAA on 2009-01-15
Can result in massive speedups on any system that ever ends up using swap, there's a new version out now with considerable improvements.  Any chance this can make it's way into jaunty?

[https://wiki.ubuntu.com/Compcache](https://wiki.ubuntu.com/Compcache)
[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

---

### Post by jfernyhough on 2009-01-15
This should be trivial to implement as all of the details needed are on the wiki page.

I tried each of the steps simply in a terminal on my Intrepid laptop and no errors or warnings are generated.

---

### Post by mc4100 on 2009-01-15
I wonder why it never to occurred to anyone just to compress data from memory **into** memory, rather than swap it out (CPU intensive?). Sound like a good solution.

---

### Post by AndersAA on 2009-01-15
> **mc4100 said:**
> I wonder why it never to occurred to anyone just to compress data from memory **into** memory, rather than swap it out (CPU intensive?). Sound like a good solution.

That's exactly how compcache worked (and previus work doing the same thing, but that was a rather huge kernel patch and never really caught on).  The reason it's swap is you might not want all memory compressed, so it uses the fastest memory first, and the slower compressed memory when it starts running out.

---

### Post by minisori on 2009-01-15
This remind me the old windows 95 memory compressors, they ended to be slower due to continuous fragmentation, zipping and unzipping. It's very probably systems with low memory = slow cpu too. Maybe nowadays works better with comps with very little memory. But With 1 gb, in a regular desktop with a regular use, and a good setup of the swappiness, it's more like probably you will never use swap. And with more, you can even put the tmp folder in ram for a big boost in general, very noticeable when compressing and uncompressing big files).

---

### Post by AndersAA on 2009-01-15
It'll always be faster than swapping, and that's what it's used to prevent.  It's not (currently atleast) used for io cache etc.

---

### Post by marmuta on 2009-01-16
> **AndersAA said:**
> Can result in massive speedups on any system that ever ends up using swap, there's a new version out now with considerable improvements.  Any chance this can make it's way into jaunty?

An update would be great to have. I've tried compcache a few times but it consistently locked up the system when I stressed it. Compcache-0.5 may have fixed that:
[http://code.google.com/p/compcache/issues/detail?id=19](http://code.google.com/p/compcache/issues/detail?id=19)

---

### Post by AndersAA on 2009-01-16
> **marmuta said:**
> An update would be great to have. I've tried compcache a few times but it consistently locked up the system when I stressed it. Compcache-0.5 may have fixed that:
[http://code.google.com/p/compcache/issues/detail?id=19](http://code.google.com/p/compcache/issues/detail?id=19)

as stated in the bug that has been resolved atleast.

---

### Post by marmuta on 2009-01-17
I've filed [#318100 - Please update compcache to new upstream version 0.5]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318100"). 
I hope it gets picked up amongst the huge bug list for linux.

---

### Post by jfernyhough on 2009-01-24
I've just enabled it. I missed the point of the wiki - I didn't realise it has already been implemented and included in Intrepid.

All you need to do is
$ gksudo gedit /etc/initramfs-tools/initramfs.conf

Change the value of COMPCACHE_SIZE. I'm going to try "50 %".

Save.

$ sudo update-initramfs -u

And that should be that.

---

### Post by karlmp on 2009-01-24
thanks jfernyhough

---

### Post by TheLions on 2009-01-24
> **minisori said:**
> This remind me the old windows 95 memory compressors, they ended to be slower due to continuous fragmentation, zipping and unzipping. It's very probably systems with low memory = slow cpu too. Maybe nowadays works better with comps with very little memory. But With 1 gb, in a regular desktop with a regular use, and a good setup of the swappiness, it's more like probably you will never use swap. And with more, you can even put the tmp folder in ram for a big boost in general, very noticeable when compressing and uncompressing big files).

how to put temp folder in ram? (in Intrepid)

---

### Post by marmuta on 2009-01-24
> **jfernyhough said:**
> 
And that should be that.

Almost...;)
Try this:
stress --vm-bytes 512M -m 1
and slowly increase m until it uses a good portion of the swap space. Always froze the system after like 5-10 seconds with perhaps a quarter of the swap used.
But who knows, maybe it's my PC and I just need a new one too.

---

### Post by marmuta on 2009-01-24
> **TheLions said:**
> how to put temp folder in ram? (in Intrepid)

I have this in my fstab:
```
tmp            /tmp tmpfs defaults,noexec,mode=0777 0 0

```

---

### Post by TheLions on 2009-01-24
> **marmuta said:**
> I have this in my fstab:
```
tmp            /tmp tmpfs defaults,noexec,mode=0777 0 0

```

thanks!

---

### Post by minisori on 2009-01-24
Use mode=1777 better, (in case you are not the only user in the comp).
Also you can tell the amount of ram you want to use, for example size=1024M.

---

### Post by marmuta on 2009-01-25
> **minisori said:**
> Use mode=1777 better, (in case you are not the only user in the comp).

Thanks, using 1777 now.

---

### Post by jfernyhough on 2009-02-25
I think this has been causing some freezes on my Intrepid laptop. I've recently started running WinXP in VirtualBox and every time I try to actually use the system it locks up - hard. Going to remove compcache and see if it still happens.

---

### Post by jfernyhough on 2009-02-25
Yeah, that fixed it..

---

