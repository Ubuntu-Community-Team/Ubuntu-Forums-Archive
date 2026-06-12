---
title: "Is linux-image-server SMP?"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by GarthK on 2006-09-15
The title pretty well covers it. Which image to select for a Dual-Core, Intel CPU based server? For a P4 with HT server? Is linux-server-image really better suited to an SMP server box than one of the 686 images with SMP? Unfortunately, none of the server image package pages indicate which processor architecture the image is optimized for.

Too many choices...

Thanx,
Garth

---

### Post by GarthK on 2006-09-27
No takers? I'm still trying to find this out but have had no success so far. As of now I intend to use the linux-686-smp kernel on all (server or desktop) boxes with P4-HT or above.

If you know, let me know.

Thanx,
Garth

---

### Post by alephant on 2006-09-29
Garth, the difference between the two seems to be mainly some optimizations which are made to make the "server" kernel more appropriate for non-desktop systems.

A diff of the .config files for 2.6.15-27 indicates the following:

  - io schedulers: 686 uses AS, server uses deadline

  - server has what look to be some optimizations for generic "server" chips

  - kernel preemption is disabled/reduced in server -- this will probably (adversely) impact desktop experience

  - server has support for much more RAM

  - server has a higher interrupt polling frequency -- along with preemption, this is probably the most user-impacting difference.  server will most likely have worse desktop interactivity due to a less-frequent interrupt poll -- but conversely, will likely have better "raw" CPU numba crunchin

  - server has some cluster filesystem options set.


Bear in mind that I've not referenced any of the kernel docs when writing this :-o  Any kernel folks care to elaborate?

Also, it bears noting that .config can change drastically between versions... I think that rather than serving as a canonical guide to functional difference, this analysis should expose the *intent* behind the two kernels: 686 is for modern, cutting-edge CPUs; server is for 686 where you don't care about desktop interactivity but do care about ekeing the absolute most out of your big huge expensive hardware.

HTH

---

### Post by GarthK on 2006-09-30
Thanx much for the response! It answers several questions I had but, as usual, brings up others. Most all of my servers act as VMWare hosts for other virtual machines, some VMs are themselves servers (database or web server, for example) and at least one supports a W2K Terminal Server environment. All are working well but I'm trying to figure out which is the best host linux image to use. This may vary depending on the type of VMs running on the machine so this might not lend itself to a simple "Use 686-smp in all cases" approach.

Your feedback has provided valuable info. Now I'll just observe the behavior and see what happens.

Thanx again,
Garth

---

