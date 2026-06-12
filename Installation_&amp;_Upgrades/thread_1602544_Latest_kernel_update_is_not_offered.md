---
title: "Latest kernel update is not offered"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2010-10-21
Hi,

I've read on the Ubuntu USN mailing list that a new Linux kernel is out that fixes some security issues. The new version for Ubuntu 10.04 is linux-image-2.6.32-[COLOR=DarkRed]**25**[/COLOR]-server. I have currently installed linux-image-2.6.32-[COLOR=DarkRed]**23**[/COLOR]-server. There is no such new package in my Synaptic package manager and not in the Update manager, not even if I update manually. Is the new kernel still out there is has it been revoked or something? Why can't I get it?

I've also noticed that the kernel image linux-image-2.6.[COLOR=DarkGreen]**35**[/COLOR]-22-server is available in Synaptic. From the USN mail I think this is the Ubuntu 10.10 kernel. It only features granted updates for a much shorter period of time. But could I upgrade to that kernel by simply installing the package? Or would it lead to problems?

---

### Post by P4man on 2010-10-21
You can find them all here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Im not sure which ones are officially released, but its possibly your mirror hasnt caught up yet. I would be very careful installing kernels like that on a server though, at the very least make sure you have an old kernel to fall back on. And do not install kernels for maverick on lucid, it will cause problems.

---

