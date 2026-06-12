---
title: "Xorg (EE) Suspending ALGLX clients for VT switch"
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by MrMe01 on 2015-10-09
Hi folks,

I'm having issues with Xorg. Startx doesn't run on system boot complete, instead I boot to the CLI login prompt. When I type startx, the screen flashes and then I get the error message

```
(EE) Suspending ALGLX clients for VT switch
```

I have the Xorg.0.log, do I post it in it's entirety, or just the lines with (EE)? Please advise.

---

### Post by MrMe01 on 2015-10-09
Well, after waiting a while for a reply, I'm taking the liberty and posting the (EE) parts of the log. In cleaning up the log in order to post it, I noticed that it's missing drivers.

```

[   659.843] (EE) Failed to load module "ati" (module does not exist, 0)
[   659.842] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   659.845] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   659.846] (EE) Failed to load module "vesa" (module does not exist, 0)
[   659.847] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   659.848] (EE) Failed to load module "ati" (module does not exist, 0)
[   659.850] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   659.851] (EE) Failed to load module "vesa" (module does not exist, 0)
[   660.823] (EE) 0: /usr/bin/X (xorg_backtrace+0x52) [0xb76a1002]
[   660.823] (EE) 1: /usr/bin/X (0xb74ff000+0x1a6222) [0xb76a5222]
[   660.823] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb74dabc8]
[   660.823] (EE) 3: /usr/lib/xorg/modules/drivers/modesetting_drv.so (0xb6b6e000+0x7513) [0xb6b75513]
[   660.823] (EE) 4: /usr/bin/X (0xb74ff000+0xbaab8) [0xb75b9ab8]
[   660.823] (EE) 5: /usr/bin/X (0xb74ff000+0xc5388) [0xb75c4388]
[   660.823] (EE) 6: /usr/bin/X (0xb74ff000+0xc3ecb) [0xb75c2ecb]
[   660.824] (EE) 7: /usr/bin/X (miPointerUpdateSprite+0x25d) [0xb768bedd]
[   660.824] (EE) 8: /usr/bin/X (0xb74ff000+0x18d141) [0xb768c141]
[   660.824] (EE) 9: /usr/bin/X (0xb74ff000+0xd2279) [0xb75d1279]
[   660.824] (EE) 10: /usr/bin/X (0xb74ff000+0x11f034) [0xb761e034]
[   660.824] (EE) 11: /usr/bin/X (0xb74ff000+0x46e31) [0xb7545e31]
[   660.824] (EE) 12: /usr/bin/X (WindowHasNewCursor+0x3b) [0xb754733b]
[   660.824] (EE) 13: /usr/bin/X (ChangeWindowAttributes+0xb7c) [0xb756cfec]
[   660.824] (EE) 14: /usr/bin/X (0xb74ff000+0x37c49) [0xb7536c49]
[   660.824] (EE) 15: /usr/bin/X (0xb74ff000+0x3def6) [0xb753cef6]
[   660.825] (EE) 16: /usr/bin/X (0xb74ff000+0x4214f) [0xb754114f]
[   660.825] (EE) 17: /usr/bin/X (0xb74ff000+0x2be3a) [0xb752ae3a]
[   660.825] (EE) 18: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xde) [0xb70ae72e]
[   660.825] (EE) 19: /usr/bin/X (0xb74ff000+0x2be78) [0xb752ae78]
```

I'm going to get those drivers and try again, if I still have issues I will update this post, otherwise I'll mark it as solved.

---

### Post by MrMe01 on 2015-10-09
Fixed. apt-get install xserver-xorg-video-all worked

---

