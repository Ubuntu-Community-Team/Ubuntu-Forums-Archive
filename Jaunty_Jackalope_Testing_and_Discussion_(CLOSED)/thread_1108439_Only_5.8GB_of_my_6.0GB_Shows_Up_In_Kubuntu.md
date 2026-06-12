---
title: "Only 5.8GB of my 6.0GB Shows Up In Kubuntu"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-03-27
I have both Windows XP x64 and Kubuntu Jaunty (also 64-bit) installed on this machine and only 5.8GB shows up. I have no shared memory whatsoever, and XP x64 as well as the BIOS sees all 6 gigs, so is this a bug?

---

### Post by tom56 on 2009-03-27
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by jlacroix on 2009-03-27
> **tom56 said:**
> [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

That doesn't relate to my situation. Thanks anyway though.

---

### Post by jlacroix on 2009-03-27
Also I should mention that Kubuntu seen all of my RAM until I upgraded to 6GB. When I had 2GB, it say exactly 2GB. When I added more RAM, everything else shows 6GB except Kubuntu. I have tested my RAM.

---

### Post by jeremyjjbrown on 2009-03-27
Ext3 saves a percentage of hd space for it's own uses. It's way to high on most partitions. you can find instructions on how to lower the percentage if you google.

---

### Post by jlacroix on 2009-03-27
> **jeremyjjbrown said:**
> Ext3 saves a percentage of hd space for it's own uses. It's way to high on most partitions. you can find instructions on how to lower the percentage if you google.

I'm referring to RAM though, is that related?

---

### Post by jeremyjjbrown on 2009-03-27
Sorry, no.

I should read more carefully. ;)

---

### Post by tom56 on 2009-03-27
> **jlacroix said:**
> That doesn't relate to my situation. Thanks anyway though.

Really? Did you even read it? My system has 1gig of memory installed, but System Monitor says I have 938.4Mib. Admittedly I can't do these sums myself, but I assume this is the cause of the "problem".

---

### Post by ktp on 2009-03-27
Try this:

 free -b

I had noticed mine only showed 5840996 kilobytes but looking at in byte it shows 5981179904; bite and byte conversion?

---

### Post by kiddo on 2009-03-27
This is the usual unit (base 2 vs S.I., or base 2 vs base 10, or some crap like that) problem. I have 4 GB of ram, for example, and gnome-system-monitor reports it as 3.9 Gib.

Be aware that I needed to use the "server" kernel to see it all, since I'm on a 32 bits system (otherwise I'd only see 3.2 Gib). But on a 64 bits system, you shouldn't be affected. I guess your 5.8/6.0 sounds normal to me.

---

### Post by jlacroix on 2009-03-27
> **ktp said:**
> Try this:

 free -b

I had noticed mine only showed 5840996 kilobytes but looking at in byte it shows 5981179904; bite and byte conversion?

Here is what that showed:
```
             total       used       free     shared    buffers     cached
Mem:    6180700160 1214652416 4966047744          0   53354496  422498304
-/+ buffers/cache:  738799616 5441900544
Swap:   3997474816          0 3997474816

```

I still don't really understand, with Kubuntu, when I had 2GB, it showed exactly 2GB.

---

### Post by tom56 on 2009-03-28
> **jlacroix said:**
> Here is what that showed:
```
             total       used       free     shared    buffers     cached
Mem:    6180700160 1214652416 4966047744          0   53354496  422498304
-/+ buffers/cache:  738799616 5441900544
Swap:   3997474816          0 3997474816

```

I still don't really understand, with Kubuntu, when I had 2GB, it showed exactly 2GB.

Ok, this is the last time I will try to explain this. There are different ways of counting size of electronic storage (such as hard drives and RAM). This stems from the fact that some people think you should count in one base (base 10, the way human beings count in day-to-day life - look at your hands to understand why), and some people another (using base two, which is how a computer sees things).

Kiddo has it right.

---

### Post by jlacroix on 2009-03-28
> **tom56 said:**
> Ok, this is the last time I will try to explain this. There are different ways of counting size of electronic storage (such as hard drives and RAM). This stems from the fact that some people think you should count in one base (base 10, the way human beings count in day-to-day life - look at your hands to understand why), and some people another (using base two, which is how a computer sees things).

Kiddo has it right.

I'm not saying you guys are wrong, I'm just having trouble understanding it. Reason being, my laptop has 4GB of RAM and it shows exactly 4096MB. My desktop when it had 2GB showed exactly 2048MB. It seems to only show less once I crossed the 5GB barrier.

---

### Post by eyelessfade on 2009-03-28
My laptop with 2GB shows 2013MB so your argument falls.
My other computer shows: 7892MB.

---

### Post by jlacroix on 2009-03-28
> **eyelessfade said:**
> My laptop with 2GB shows 2013MB so your argument falls.
My other computer shows: 7892MB.

One of my other computers showed 2013MB, but I found that to be due to ACPI reserved memory or something similar.

---

### Post by aaronb on 2009-03-28
I think the 5.8GB instead of 6.0GB issue is caused by the BIOS reserving memory for its own usage. My PC has 2048MB of ram however only 1991MB is available for Linux to use due to the BIOS. I believe its the Intel QST (Quiet System Technology) causes this in my case.

I can turn QST off and use "legacy" fan control and have more memory availible to Linux.
[B]
The below is with QST on:[/B]
```

             total       used       free     shared    buffers     cached
Mem:          1991        922       1069          0         22        342
-/+ buffers/cache:        557       1434
Swap:         5828          0       5828

```
[B]
The below is with QST off:[/B]
```
             total       used       free     shared    buffers     cached
Mem:          2007        814       1193          0         17        303
-/+ buffers/cache:        493       1514
Swap:         5828          0       5828
```

As you can see more RAM is available for Linux to use at the expense of added noise.

From your signature you have an AMD system so the exact cause of the "missing" memory may be different. So if you want the full 6GB (or at least more of it) then it may be worth looking at your BIOS settings and your log files.

When RAM is involved base 2 is normally used so 2GB is 2,147,483,648 bytes or 2*2^30 bytes not 2*10^9 bytes.

---

### Post by tripolitan on 2009-03-28
the link that TOM56 provided, is very relevant.

> "The exact capacity of a given drive is usually some number above or below the class designation." 

It is very simple. Since it is very possible that the original 2GB were not exactly 2GB we can conclude that Kubuntu may not have been indicating the EXACT RAM, even though it showed 2GB.

---

