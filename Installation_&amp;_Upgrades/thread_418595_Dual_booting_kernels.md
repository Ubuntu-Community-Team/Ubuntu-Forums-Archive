---
title: "Dual booting kernels"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by dahouse on 2007-04-22
Hi,

I'm currently running Kubuntu having recently switched from gentoo (cause it was getting to be a pain.)

With gentoo, I was able to have mulitiple kernels, but with Ubuntu, the installation was completely automated, so I have no idea how to get 2 kernels.

The reason I want 2 kernels is because I want one for pro audio  use (low latency realtime) and one for desktop use.

So, how would I set this up? I haven't installed the realtime kernel yet in fear of screwing up and deleting the non real time one.

---

### Post by mlind on 2007-04-22
> **dahouse said:**
> Hi,

I'm currently running Kubuntu having recently switched from gentoo (cause it was getting to be a pain.)

With gentoo, I was able to have mulitiple kernels, but with Ubuntu, the installation was completely automated, so I have no idea how to get 2 kernels.

The reason I want 2 kernels is because I want one for pro audio  use (low latency realtime) and one for desktop use.

So, how would I set this up? I haven't installed the realtime kernel yet in fear of screwing up and deleting the non real time one.

You'll just have to install a new kernel. Ubuntu will automatically update grub menu when you install kernel from APT repository. 
If you want to use shared kernels (gentoo and Ubuntu), you need to have shared /boot partition.


For newest lowlatency kernel
```

sudo aptitude install linux-image-lowlatency

```

---

### Post by dahouse on 2007-04-22
So grub will show up with 2 options?

---

### Post by mlind on 2007-04-22
> **dahouse said:**
> So grub will show up with 2 options?

By default, Ubuntu's grub menu contains also recovery menu items for all installed kernels and a memtest86 option.

You can see the grub kernel list and options by looking /boot/grub/menu.lst, but don't edit automated kernel list. Edit options instead and then invoke sudo update-grub.

---

### Post by dahouse on 2007-04-22
Ok, so I did the install, but how do I configure grub so that a list of options show up (like the purple gui of grub that come with my gentoo installation) that let me choose the kernel I want to load and what the default kernel option is.

---

### Post by scooper on 2007-04-23
> **dahouse said:**
> ... how do I configure grub so that a list of options show up ...

Did you try "sudo update-grub"?  This is what refreshes the contents of menu.lst.

---

