---
title: "Upgrade to kernel 2.6.33"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by nomadewolf on 2010-03-11
Hi!
I'm running Ubuntu 9.10 and i successfully updated my kernel up to 2.6.32... But now 2.6.33 is out there and i would like to update to that version, however, my proprietary drivers get broken, and i can't even reinstall them manually... So i end up loosing 3D, which sucks...
Has anyone successfully updated to this kernel version, how?

---

### Post by solar george on 2010-03-11
Is there a reason you *need* kernel .33? ("Its new" is not a reason to need it). If not you'd be much better off waiting untill it makes its way into ubuntu by way of the repositories.

---

### Post by slakkie on 2010-03-11
You can find the new kernel in Lucid (which is still in development, releases 29th of april iirc).

Or here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by nomadewolf on 2010-03-12
> **solar george said:**
> Is there a reason you *need* kernel .33? ("Its new" is not a reason to need it). If not you'd be much better off waiting untill it makes its way into ubuntu by way of the repositories.

I can live my life without it, but i experience slowness in my desktop with the ATI card, and i would like to keep 3D and have a fast/normal Desktop experience. So i would like to try out the .33 kernel to see if i get any improvement...

---

### Post by nomadewolf on 2010-03-12
> **slakkie said:**
> You can find the new kernel in Lucid (which is still in development, releases 29th of april iirc).

Or here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/")

I know where to find the kernel, and how to install it. But i can't install the ATI (or NVidia) proprietary drivers... I can install the drivers in .31 and .32, but not .33...

Oh, and i read somewhere that Lucid was projected to ship with .32 kernel with some backports... Unless that changes, there will be no .33 kernel in Lucid...

---

### Post by slakkie on 2010-03-12
You are right, I was expecting it to hit lucid, but looking at the kernels available in lucid it proves me wrong:

```

$ dpkg -l | grep linux-image
ii  linux-image-2.6.32-11-generic              2.6.32-11.15                                    Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-12-generic              2.6.32-12.17                                    Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-13-generic              2.6.32-13.18                                    Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-14-generic              2.6.32-14.20                                    Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-generic                        2.6.32.14.15                                    Generic Linux kernel image

```

---

### Post by sgosnell on 2010-03-12
I use 2.6.33, because it works better on my EEE-PC.  I haven't tried to install any proprietary drivers, though, since I don't need them with the newer kernel.

---

### Post by lsbe on 2010-03-26
.33.1 on my acer aspire one cuts the boot time nicely and fixes a problem i was having with the wifi light not flashing. currently working on stripping it down for my netbook(last attempt failed horribly xD thank god for the kernel choice at boot)

---

