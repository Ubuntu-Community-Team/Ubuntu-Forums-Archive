---
title: "what happened to amd k7 kernel?"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by ChrisC on 2008-07-13
Hi all -

This weekend I'm upgrading my desktop from 6.06 to 8.04.  I've kept just my /home partition and am otherwise doing a completely fresh install of 8.04.  One of the early steps in my installation process is to install the amd k7 kernel.  However, looking in Synaptic, the linux-image-k7 entries all say:

"Upgrade dummy package.  Can be removed"

Soooo ... Do I still use those packages to get an AMD K7 kernel, or is there some other method?

Surprisingly, I found nothing about this in searching the forum or even googling.  I'd think it'd be a common question ... I mean, the hardware isn't THAT old :)

[FYI, this is a 32-bit install, not 64-bit.  Yes, the processor is 64-bit, but I'm running it in 32-bit mode and do not care to mess with 64-bit, thanks]

---

### Post by ChrisC on 2008-07-13
I'm sitting idle on some key parts of my installation until I know the answer to this.  Some installs (e.g. drivers) get upset if you later change the kernel, so I'd like to get this amd-k7 kernel issue resolved before moving on.  Anyone?

---

### Post by coffeecat on 2008-07-13
I can't give you a definitive answer, but I seem to remember that somewhere along the line that the k7 kernel was abandoned in favour of a generic one.

That's not very helpful but what I can tell you is that I am posting from a machine with an AMD Athlon 64 X2 4200+ processor and it's running fine with the generic kernel - the 32-bit one. I can't be bothered with the 64-bit version - I haven't got enough memory to make it worthwhile anyway.

Synaptic is showing for linux-image-2.6.24-19, the -generic, -386, -openvz, -rt, -server, -virtual and -xen versions.

---

### Post by sdennie on 2008-07-13
At one point I believe that many of the kernel images were rolled together because it was easier to maintain fewer kernels and there was no real difference between many of them anyway.  I would just use linux-image-generic as it's the default kernel and supports the functionality that the vast majority of users need.

---

### Post by ChrisC on 2008-07-13
Aha.  Some searching just now led me to these corroborating tidbits:

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

"My recommendation is that we phase out these additional kernel builds, which
I expect will save us a great deal of developer time, buildd time, archive
storage and bandwidth."  (and then lots of discussion follows from there)

[http://tuxicity.wordpress.com/2007/08/13/linux-ubuntu-2622-9-generic-vs-linux-ubuntu-2622-9-my-architecture/](http://tuxicity.wordpress.com/2007/08/13/linux-ubuntu-2622-9-generic-vs-linux-ubuntu-2622-9-my-architecture/)

"[yes, arch kernel is snappier and faster, but ...] Is it worth the effort for the average user? No absolutely not, If I would use Ubuntu tomorrow with the generic kernel I probably would not notice the difference. If you like tweaking, go for it."

OK then!  I'll cross the k7 kernel install off my checklist.  Now. on to the nvidia driver installation ...

---

