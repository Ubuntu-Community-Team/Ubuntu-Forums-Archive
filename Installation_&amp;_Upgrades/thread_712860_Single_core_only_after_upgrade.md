---
title: "Single core only after upgrade"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Claw on 2008-03-02
I was running Gusty on this computer (which has  a AMD Athlon dual core processor) and just upgraded to Hardy. Before the upgrade, the system was recognising that the computer had two processor cores, but now, it doesn't appear to. dmesg | grep CPU yields the following output:
```
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] Initializing CPU#0
[   22.155199] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.235395] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   22.235402] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.235404] CPU: L2 Cache: 512K (64 bytes/line)
[   22.235407] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   22.235422] CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[   22.766826] Switched to high resolution mode on CPU 0

```

The kernel that was installed was:
```
2.6.24-11-386 #1 Fri Feb 29 21:28:00 UTC 2008 i686 GNU/Linux
```

Do I have to install a different kernel for this to work, and if so, should I submit a bug report?

Thanks,

-Stephen

---

### Post by Pumalite on 2008-03-02
You need 24-10 generic SMP (686)

---

### Post by Handssolow on 2008-03-02
Using the terminal the command
uname -r
probably shows you have the 386 kernel rather than generic which you need to use both AMD cores.

Before you finally edit boot/grub/menu.lst try pressing ESC after post to enter the GRUB menu, here hopefully you'll see a generic kernel available. If you're successfully check uname -r again to see if you're running generic. Afterwards you can use sudo gedit /boot/grub/menu.lst to ## out the 386 kernels so you'll have generic as the top choices.

---

### Post by Claw on 2008-03-02
I do have "kernel 2.6.24-10-generic" but that wouldn't boot for me - it just sat there with the progress bar going back and forth.

I'll try again soon, along with 2.6.22

---

### Post by matjan on 2008-03-02
The same thing happened to me.
I did the hardy update this morning from 2.6.24-10-generic to 2.6.24-11-386 and now only one core on my core 2 quad is recognized.

```
Mar  2 12:37:56 quadpc kernel: [    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
```

When I try to run the machine using 2.6.24-10-generic, graphics are screwed up. 
My guess is that this is due to the fact that the nvidia-glx-new package was also updated and therefore will only work properly with 2.6.24-11-386. Is this what is going on?

---

### Post by Pumalite on 2008-03-02
Hardy Heron is in development.

---

### Post by Claw on 2008-03-03
Well, neither of them worked (one wouldn't start X and the other just dropped me to a Built-in shell), but it looks like I just got a generic kernel in an update, so I'll see how that works out.

> **Pumalite said:**
> Hardy Heron is in development.
Yes, that's why I though of submitting a bug report.

---

### Post by scorpion-kde on 2008-03-04
I just ran updates, and aptitude wants to install linux-image-2.6.24-11-386 because of nvidia-glx-new.  I cannot tell why it thinks it needs the 386 kernel for nvidia-glx-new, but when this happened on a different computer, I was able to remove the 386 kernel, install the latest generic kernel, and have my nvidia drivers still work.

---

