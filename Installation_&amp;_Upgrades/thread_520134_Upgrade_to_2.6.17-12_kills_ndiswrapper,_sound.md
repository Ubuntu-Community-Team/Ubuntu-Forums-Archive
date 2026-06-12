---
title: "Upgrade to 2.6.17-12 kills ndiswrapper, sound"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by keflavich on 2007-08-07
I recently upgraded from 2.6.17-11 to 2.6.17-12 running Edgy on a Compaq v6000 laptop.  After the reboot, ndiswrapper failed to load (my wireless card would not turn on) and sound failed.  Those two problems were very difficult to deal with on the original install on this machine, so I was worried, but I figured out that the new kernel, loading with the same options of "noapic pnpbios=off", was responsible.

Can anyone suggest what changed might have caused the failure?  Should I be using different startup options with the new kernel?

Thanks,
Adam

---

### Post by fredj on 2007-08-08
Ndiswrapper often seems to fail with kernel updates. If you try booting into the previous kernel
you will probably find that it works again.
The answer to this problem is to remove ndiswrapper with modprobe -r ndiswrapper and 
re-install it. If you compiled ndiswrapper yourself then you will need to download the kernel
headers for your latest kernel and recompile and reinstall the windows drivers.
I don't have any ideas about the sound problem.

---

### Post by keflavich on 2007-08-10
Thanks, I suppose it makes sense that I have to recompile ndiswrapper with a new kernel since I had to compile it with the last one... so I won't be upgrading my kernel, that process was far too painful.

Adam

---

### Post by fredj on 2007-08-11
Once you've done it a few times (make notes), you can do it in five minutes. So its not so
painful.

---

