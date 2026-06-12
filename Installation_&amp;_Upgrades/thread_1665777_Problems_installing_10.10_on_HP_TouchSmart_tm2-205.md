---
title: "Problems installing 10.10 on HP TouchSmart tm2-2050er"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by shutyaev on 2011-01-12
First problem was when booting from cd - black screen. After googling I found out that this bug is well known on HP TouchSmart and the solution is to close and reopen the lid. That helped. The installation was normal, nothing unusual. After restart on first boot I get Oops (text below). Tried to install both with and without online updates during installation.

Details: Ubuntu 10.10 Desktop x64, laptop HP TouchSmart tm2-2050er (with touchscreen, which worked fine even in the installation environment).

Output (hope there are no misprints as I had to retype it manually):

```

[    5.269844] agpgart-intel 000:00:00.0 AGP aperture is 256M @ 0xb0000000
[    5.269887] intel ips 000:00:1f.6: No CPUID match found.
[    5.269902] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
[    5.269907] IP: [<ffffffffa00fd3c6>] ips_detect_cpu+0x76/0x1d0 [intel_ips]
[    5.269918] PGD 11601a067 PUD 11602b067 PMD 0
[    5.269922] Oops: 0000 [#1] SMP
[    5.269925] last sysfs file: /sys/devices/virtual/misc/agpgart/uevent
[    5.269929] CPU 1
[    5.269931] Modules linked in: soundcore intel_ips(+) snd_page_alloc hp_wmi(+) v412_compat_ioctl32 usbhid i2c_algo_bit hid intel_agp(+) psmouse serio_raw lp wacom parport usb_storage ahci libahci r8169 mii
[    5.269947]
[    5.269951] Pid: 498, comm: modprobe Not tainted 2.6.35-22-generic #33-Ubuntu 1486/HP TouchSmart tm2 Notebook PC
[    5.269955] RIP: 0010:[<ffffffffa00fd3c6>]  [<ffffffffa00fd3c6>] ips_detect_cpu+0x76/0x1d0 [intel_ips]
[    5.269963] RSP: 0018:ffff880118211c48  EFLAGS: 00010202
[    5.269966] RAX: 0000000000580058 RBX: 0000000000000000 RCX: 0000000000580058
[    5.269968] RDX: 0000000000000000 RSI: ffff880118211c64 RDI: 0000000000580058
[    5.269971] RBP: ffff880118211c88 R08: 0000000000000000 R09: 000000000000000a
[    5.269974] R10: 0000000000000006 R11: 0000000000000003 R12: 0000000000580058
[    5.269977] R13: ffff8801174863c0 R14: ffff8801165d3090 R15: 00000000fffffff4
[    5.269981] FS:  00007fc90c159700(0000) GS:ffff880001e40000(0000) knlGS:0000000000000000

```

---

### Post by Favux on 2011-01-12
Hi shutyaev,

While it's saying it can't identify the CPU my guess is it is still the dual graphics chipset problem.

Please see my post #3 on this thread:  [http://ubuntuforums.org/showthread.php?t=1661112](http://ubuntuforums.org/showthread.php?t=1661112)

---

### Post by shutyaev on 2011-01-12
Thanks for help, but I'm not quite sure that this is the cause of the problem. However I found something out and it seems like the cause of my problem is this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631)
As you can see it was fixed with the new kernel version. My question is how can I use this update (since my ubuntu is not actually working)? If I download & burn the installation image will it contain the latest kernel version? If not - how can I get to install the new kernel with the old installation image?

---

### Post by fashion_m on 2011-09-28
Hello, I consider buying HP Touchsmart TM2 and I want to ask whether the Ubuntu issues with this laptop have been solved yet?

---

### Post by Favux on 2011-09-28
Hi fashion_m,

Welcome to Ubuntu forums!

This is the thread you probably want to post on and look over:  [http://ubuntuforums.org/showthread.php?t=1716403](http://ubuntuforums.org/showthread.php?t=1716403)

---

