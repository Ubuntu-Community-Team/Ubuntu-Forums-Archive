---
title: "ASUS K50IN Notebook: no go since beta1"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gecka on 2010-04-09
Hello,

I was hoping beta2 will solve it, but unfortunately: no.

Here is what I get loading ubuntu lucid live cd on my ASUS K50IN Notebook:

[http://www.youtube.com/watch?v=nsWnozx8sn8](http://www.youtube.com/watch?v=nsWnozx8sn8)

Anyone has an idea of what could be wrong?

---

### Post by gecka on 2010-04-12
And Fail Safe graphic mode has disappeared in lucid...

---

### Post by gecka on 2010-04-14
How can I report the bug I am suffering? Launchpad asks for the package name.

One more point on my problem, when the LiveCD has loaded I hear the session opening sound and I can switch to command line using CTRL+ALT+F1.

Is there anything I can check from the command line to find the package  failing?

Regards

---

### Post by cariboo on 2010-04-14
At the initial screen press the any key :), there is no safe graphics mode anymore, but if you press F6 and select nomodeset, you should be able to boot to a desktop.

---

### Post by gecka on 2010-04-14
> **cariboo907 said:**
> At the initial screen press the any key :), there is no safe graphics mode anymore, but if you press F6 and select nomodeset, you should be able to boot to a desktop.

Thanks for taking time to reply but it didn't help: same result with nomodeset activated.

I had a look to syslog and found that
```
pr 14 17:10:47 ubuntu kernel: [  200.930030] Process Xorg (pid: 2383, threadinfo ffff88011ad62000, task ffff880116e3dbc0)
Apr 14 17:10:47 ubuntu kernel: [  200.930032] Stack:
Apr 14 17:10:47 ubuntu kernel: [  200.930034]  ffff88011ad63da8 0000000000000001 ffff88011ab80000 ffff88011ab80000
Apr 14 17:10:47 ubuntu kernel: [  200.930037] <0> ffff88011ad63dd8 ffffffffa00b02d7 ffff88011ab800c8 ffff880119e73920
Apr 14 17:10:47 ubuntu kernel: [  200.930041] <0> ffff880119e73800 ffff88011ab80000 ffff880119e73820 ffff88011ab800c8
Apr 14 17:10:47 ubuntu kernel: [  200.930046] Call Trace:
Apr 14 17:10:47 ubuntu kernel: [  200.930056]  [<ffffffffa00b02d7>] nouveau_mem_close+0x27/0x190 [nouveau]
Apr 14 17:10:47 ubuntu kernel: [  200.930065]  [<ffffffffa00ad82b>] nouveau_card_takedown+0xfb/0x1b0 [nouveau]
Apr 14 17:10:47 ubuntu kernel: [  200.930074]  [<ffffffffa00ad988>] nouveau_lastclose+0x28/0x30 [nouveau]
Apr 14 17:10:47 ubuntu kernel: [  200.930091]  [<ffffffffa00358e9>] drm_lastclose+0x49/0x310 [drm]
Apr 14 17:10:47 ubuntu kernel: [  200.930101]  [<ffffffffa003684e>] drm_release+0x3be/0x4f0 [drm]
Apr 14 17:10:47 ubuntu kernel: [  200.930107]  [<ffffffff811441a5>] __fput+0xf5/0x210
Apr 14 17:10:47 ubuntu kernel: [  200.930110]  [<ffffffff811442e5>] fput+0x25/0x30
Apr 14 17:10:47 ubuntu kernel: [  200.930113]  [<ffffffff811403dd>] filp_close+0x5d/0x90
Apr 14 17:10:47 ubuntu kernel: [  200.930116]  [<ffffffff811404c7>] sys_close+0xb7/0x120
Apr 14 17:10:47 ubuntu kernel: [  200.930122]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Apr 14 17:10:47 ubuntu kernel: [  200.930124] Code: 0d fe ff 48 89 df 89 45 e8 e8 bd d6 fd ff 8b 45 e8 48 83 c4 18 5b c9 c3 0f 1f 00 55 48 89 e5 41 54 53 48 83 ec 10 0f 1f 44 00 00 <8b> 97 e0 01 00 00 31 c0 4c 8b 67 08 48 89 fb 83 ea 01 85 d2 89 
Apr 14 17:10:47 ubuntu kernel: [  200.930155] RIP  [<ffffffffa00b6b50>] nouveau_bo_unpin+0x10/0xe0 [nouveau]
Apr 14 17:10:47 ubuntu kernel: [  200.930165]  RSP <ffff88011ad63d78>
Apr 14 17:10:47 ubuntu kernel: [  200.930166] CR2: 00000000000001e0
Apr 14 17:10:47 ubuntu kernel: [  200.930190] ---[ end trace ba6713bd390fd2de ]---
Apr 14 17:10:47 ubuntu gdm-binary[1569]: WARNING: GdmDisplay: display lasted 1,406229 seconds
Apr 14 17:10:47 ubuntu acpid: client 2383[0:0] has disconnected
Apr 14 17:10:47 ubuntu acpid: client connected from 2468[0:0]
Apr 14 17:10:47 ubuntu acpid: 1 client rule loaded
Apr 14 17:10:48 ubuntu gdm-binary[1569]: WARNING: GdmDisplay: display lasted 0,427046 seconds
```

So it might be related to the nouveau nvidia driver ?

---

### Post by gecka on 2010-04-20
Solved. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/567579](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/567579)

---

### Post by gecka on 2010-04-20
[QUOTE=gecka;9150852]

---

