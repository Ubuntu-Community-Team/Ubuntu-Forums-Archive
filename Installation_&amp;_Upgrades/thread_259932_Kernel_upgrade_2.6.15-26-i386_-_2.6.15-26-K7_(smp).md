---
title: "Kernel upgrade: 2.6.15-26-i386 - 2.6.15-26-K7 (smp?)"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by RoosTa on 2006-09-18
I'm fairly new to Linux and have been dabbling with it for the past month.

I have an AMD64 X2 4200+ (Dual Core) and I'd like to enable smp.

My current system is running very stable with ATI drivers fglrx 8.28.8 and XGL/Compiz, though I'd like to get the best performance from my rig.

1) Will updating to [linux-image-2.6.15-26-K7 (and dependencies)](http://packages.ubuntulinux.org/dapper/base/linux-image-2.6.15-26-k7) kernel enable smp?

2) What impact it would have if I had to upgrade my kernel from 2.6.15-26-i386 (std ubuntu) to 2.6.15-26-K7. 

Thanks in advance.

---

### Post by anodizer on 2006-09-18
1) Yes.
2) Just do it. It is desirable to install a cpu specific kernel. Keep in mind though, you 'll have to reinstall ATi drivers (and maybe some other drivers that you have possibly compiled too), but it's worth the time.

---

### Post by RoosTa on 2006-09-18
Thanks for the reply.

I also noticed a K8, but I assumed its 64bit which is why I chose K7. I want to stay with 32bit since I've heard/read there are less hassles with it. 

Just a few more questions:

1)Once I've installed the kernel, does that mean I'll have to 'fix' (load drivers etc)everything in the console before starting X? In other words will I be able to boot into X? (I need to know this so that I can print out documents etc.)
2)Also if things don't work out, would I be able to select the std kernel in grub and boot up as I have been? (my previous kernel is in grub after upgrade)

---

### Post by mixmaster on 2006-09-18
There is a linux-k7-smp (from memory) psuedo-package.  If you install that you will always get the latest k7-smp kernel.  The original generic kernel will remain in your grub menu if you need to go back to it.

When I upgraded to k7 usign this package I had to make no other changes.

---

