---
title: "Compiling kernel --&gt; which CPU type to choose ?"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by sibrand on 2006-11-25
Alrighty, I want to compile the 2.6.18.3, but I don't know which CPU family I should choose in qconf. 
I've got a AMD Athlon64 3000+ (Venice), and I need a 32-bit kernel. What would you recommend ?

Thanks in advance. ;)

---

### Post by sibrand on 2006-11-25
I need to choose between
[LIST][*]Athlon/Duron/K7
[*]Opteron/Athlon64/Hammer/K8
[/LIST]
And also the standard 386; qconf marked the 686 by default.

I think K7 is recommended, but on the other hand... I've got a Athlon64 which means I should take K8. 

What to choose ? :confused:

---

### Post by dcstar on 2006-11-26
> **sibrand said:**
> I need to choose between
[LIST][*]Athlon/Duron/K7
[*]Opteron/Athlon64/Hammer/K8
[/LIST]
And also the standard 386; qconf marked the 686 by default.

I think K7 is recommended, but on the other hand... I've got a Athlon64 which means I should take K8. 

What to choose ? :confused:

If you want a 32 bit kernel, you should choose the 32 bit CPU - K7.

---

### Post by Sandriman on 2006-11-26
Choosing K8 doesn't actually mean that your kernel would be 64-bit, it just means GCC will use any possible optimizations it can, while producing a 32-bit kernel.

I always went with K8 over K7, and got quite nice results.

---

### Post by sibrand on 2006-11-26
I've taken k8, and it works like a charm. :D 

I had some troubles with the *nvidia beta drivers* and *ndiswrapper*, but I managed to solve them. 

In qconf do _not_ mark *nvidia frame buffers* in the section *graphic devices*, 'cause if you do, *nvidiafb* will block the installation procedure of the *nvidia beta driver*. 
It'll say something about *module nvidiafb conflicts with*..., but when you try to *modprobe -r* or *rmmod* nvidiafb, you'll see it's just not there. Also looked in /etc/modprobe.d and /proc/modules but nvidiafb just wasn't there.
Then I rebooted with my previous kernel, and I recompiled the 2.6.18.3, but now without the nvidia frame buffers. Rebooted in 2.6.18.3 and the beta drivers installed immediately.

For ndiswrapper I've commented everything in /etc/network/interfaces that had nothing to do with wlan0. 
Now my wireless card connects automatically on a reboot.

---

