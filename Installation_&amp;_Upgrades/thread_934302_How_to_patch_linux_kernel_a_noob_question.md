---
title: "How to patch linux kernel? a noob question"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by warnec on 2008-09-30
Hi guys. I wanted to use 64-bit version of Ubuntu 8.04, but after booting from LiveCD i got text mode with 
```

'BusyBox 1.13
```blablabla' 

instead of normal Ubuntu GUI. I switched off graphical boot, and I got error message like this :

```

ata6: classification failed
ata6: reset failed(errno: -22)

```

I think I found a solution here:

[http://bbs.archlinux.org/viewtopic.php?pid=360567#p360567](http://bbs.archlinux.org/viewtopic.php?pid=360567#p360567)

The last post says:
```

Okay, finally managed to fix this problem, and here's how I did it.
I made a bug report and someone responded with a patch quite fast.So simply get the patch, save it as a text file and patch your src/drivers/ata/ahci.c with it. (yes obviously you need to compile a custom kernel, it's really easy with ABS).
That's it, just works for me now.

```

There is the link to the patch, but I have no idea how to apply it to the kernel. Can you give me a noobproof guide how to alter the kernel which is inside the ISO file with Ubuntu 8.04 64bit ?

I cannot boot Linux, so I must do it with Windows XP which runsfine. Isthis possible?

---

### Post by christian.adeen on 2008-10-14
Hi warnec have you found a way to patch the kernel? I have the same problem. Seems like the jimcron chip on my mobo is not recogniced by the installers kernel...

---

