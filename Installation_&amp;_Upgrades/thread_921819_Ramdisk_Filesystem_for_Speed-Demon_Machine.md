---
title: "Ramdisk Filesystem for Speed-Demon Machine"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by Xanderfoxx on 2008-09-16
I have an idea that may not be original, but I believe that I have an innovative approach to this. I would like to discuss problems and possible features involving the below scenario:

Computer Hardware:


Dual CPU - (2x) Phenom Quad Core

16GB DDR2 RAM

32GB Flash drive mounted directly to motherboard as first secondary storage device - BIOS treats Flash drive as a native storage device, similarly to a HDD

...

The "innovation" lies in the way the computer boots up. (I believe I may be rehashing something. Geniuses like you would have done this already if it was feasible.)

The computer loads GRUB, which loads the Linux kernel , but during one of the earlier stages of boot, sometime after loading the kernel filesystem drivers for ext3fs and tmpfs, and before the graphical user interface loads, the kernel is instructed to create an ~8GB out of the total 16GB into a tmpfs filesystem, and copies /proc, /bin, /dev, /etc, /lib, /opt, /sbin, /srv, and /var directories to this filesystem from the 32GB Flash drive.

I imagine that 4GB is all I would need for that alone, but I'm planning on adding a 3D virtual world as a user interface (as the technology exists or can relatively easily be created). The utilities, tools, application frameworks, and all of the media, modeling, and theme data needs to be cached for this to work well, so the other 4GB is for that.

The last 8GB will contain running instantiations, as I imagine that 8GB should be enough to do that.

Before you start commenting, I know that there is a reasonably good caching subsystem, and it does a fine job, yes I know that similar setups have been tried before, but I do not believe that people have create a commercially-supported desktop operating system based on Linux that stores the entire operating system in a Ramdisk, and backs up the data when the computer is idling or shutting down, and uses the Ramdisk for advanced visualization that replaces the traditional window metaphor with a virtual world similar to what you would find in Second Life, or any major MMORPG.

If you have any comments, even those of you who love to hate on me, go ahead and tell me what you think about this.

If there are any inaccuracies or technical problems that I would face attempting to implement this, and any reccomended solutions, fire away.

Oh, and I'd rather not get comments intended to discourage me from the project completely. If you have a good reason why a project like this would be completely infeasable or impractical, tell me, but I better not see you turn around and do it yourself. That would be very unmanly.

---

