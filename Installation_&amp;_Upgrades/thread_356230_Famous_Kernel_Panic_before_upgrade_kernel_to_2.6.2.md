---
title: "Famous Kernel Panic before upgrade kernel to 2.6.20 (vanilla)"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by braintheboss on 2007-02-08
I have a hp laptop with core duo 2 and intel ICH sata controller. I have a ubuntu edgy with kernel 2.6.17.10. With old kernel the system boot. With new kernel fails. I have everything correct. The kernel was compiled without problems. I have proved the drivers SATA so much as Modules as included in the kernel. I have the disc ram to unload the modules. But it fails.


Is PIIX-ICH SATA driver the correct for my system? Is it sufficient or I have to activate some option more?

Thanks for advice.

PD. Is my first kernel compilation and I'm newber. :( Because they are such difficult things in linux? Are not 16 years developing it sufficient so that certain things work with certain "logic"?

---

### Post by quick_dudley on 2007-03-28
I've had the same problem on my father's computer (giving him a new kernel in case it has bugfixes for his soundcard driver). I was going to post a help request on here but in the middle of the night I had an idea which I will try out when I get home.
Don't compile ext3fs and disk access drivers as modules but as built-in. The If you compile them as modules you'd get a chicken-and-egg problem where the kernel needs to load the modules before it can access your filesystem, and it needs to access the filesystem before it can load the modules. (the GRUB drivers are dropped when the kernel is loaded)
 Also, in the kernel source, see Documentation/initrd.txt
make a new initrd for your new kernel, I'll be basing mine on the one that comes with edgy but adapting it to the new kernel. I'm not sure if Ubuntu works without an initrd so I'll try that as well.

---

