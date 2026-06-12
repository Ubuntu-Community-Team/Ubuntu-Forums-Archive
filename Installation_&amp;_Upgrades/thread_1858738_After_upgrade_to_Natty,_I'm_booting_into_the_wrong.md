---
title: "After upgrade to Natty, I'm booting into the wrong kernel"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by Phiwum on 2011-10-12
Hey ho.

I just upgraded by 64 bit machine to Natty tonight, but after reboot, X didn't start.  I checked the log and discovered the following:

```
Oct 12 17:20:29 leibniz kernel: [264211.670247] NVRM: API mismatch: the client has the version 270.41.06, but
Oct 12 17:20:29 leibniz kernel: [264211.670250] NVRM: this kernel module has the version 260.19.06.  Please
Oct 12 17:20:29 leibniz kernel: [264211.670251] NVRM: make sure that this kernel module and all NVIDIA driver
Oct 12 17:20:29 leibniz kernel: [264211.670252] NVRM: components have the same version.


```

I poked around for a while before deciding to see what kernel I'm running.  Here's what uname -a says:

```
Linux leibniz 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 x86_64 x86_64 GNU/Linux

```
That doesn't look right.  I think I'm supposed to be running 2.6.38.  Grub seems to agree, since /boot/grub/menu.lst contains the following:

```
## ## End Default Options ##

title           Ubuntu 11.04, kernel 2.6.38-11-generic
uuid            81d1fc92-12d6-4fe2-9d5b-852b552bb558
kernel          /boot/vmlinuz-2.6.38-11-generic root=UUID=81d1fc92-12d6-4fe2-9d5b-852b552bb558 ro quiet splash 
initrd          /boot/initrd.img-2.6.38-11-generic

title           Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid            81d1fc92-12d6-4fe2-9d5b-852b552bb558
kernel          /boot/vmlinuz-2.6.38-11-generic root=UUID=81d1fc92-12d6-4fe2-9d5b-852b552bb558 ro  single
initrd          /boot/initrd.img-2.6.38-11-generic

title           Ubuntu 11.04, kernel 2.6.35-22-generic
uuid            81d1fc92-12d6-4fe2-9d5b-852b552bb558
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=81d1fc92-12d6-4fe2-9d5b-852b552bb558 ro quiet splash 
initrd          /boot/initrd.img-2.6.35-22-generic

```

Geez, now that I look at it, the kernel I'm running must be from Lucid, not Maverick.  Weird.

Any ideas what's happening here?  How can I diagnose the issue?  The /boot directory seems to have all the relevant files (as far as I know, anyway), so what's up?

Much thanks.

---

### Post by Phiwum on 2011-10-12
I was looking through the Ubuntu pages on grub, and I saw that grub uses grub.cfg these days, rather than menu.lst.  I also see that my grub.cfg shows a modification date of June, 2010 while menu.lst shows a modification date of today.

I see references to 2.6.32-21 in grub.cfg as well, rather than to the current kernel in natty.

Surely this has something to do with the problem, but how do I get grub.cfg to update?

**NEVER MIND.  I'm using Grub rather than Grub2, so surely grub.cfg is a red herring. (?)**

---

### Post by Phiwum on 2011-10-13
I have solved the problem.  I'm convinced that the presence of an out-of-date grub.cfg was somehow causing grub 0.97 to boot into an older kernel.  I don't know why I had grub.cfg and other files used by grub2 on my machine, since I used grub 0.97, not grub2.

I thought about removing all the files that evidently shouldn't have been there, and running update-grub, but instead I chose to install grub2, since it is the preferred grub for Ubuntu.  I ran
```

sudo apt-get install grub-pc

```
This updated grub.cfg, so I rebooted.  I'm now running the right kernel, so the nvidia modules are loading properly.

No idea how my /boot/grub directory contained grub2 stuff, but no worries now.

---

