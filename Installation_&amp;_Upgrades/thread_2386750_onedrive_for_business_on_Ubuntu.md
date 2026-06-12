---
title: "onedrive for business on Ubuntu"
date: 2018-03-09
forum: Installation &amp; Upgrades
---

### Post by pema001 on 2018-03-09
Hi,

I have successfully installed O365 for business on Ubuntu 17.10 and it worked. However, after one day, one error started to appear:

```
std.utf.UTFException@/usr/lib/ldc/x86_64-linux-gnu/include/d/std/utf.d(1385): Invalid UTF-8 sequence (at index 1)
----------------
??:? [0xf18c188]
??:? [0xf18c032]
??:? [0xf18bf76]
??:? [0xf11e443]
??:? [0xf1204c6]
??:? [0xf13355b]
??:? [0xf1321c2]
??:? _D2rt6dmain211_d_run_mainUiPPaPUAAaZiZ6runAllMFZ9__lambda1MFZv [0xb5036a0e]
??:? void rt.dmain2._d_run_main(int, char**, extern (C) int function(char[][])*).tryExec(scope void delegate()) [0xb503694d]
??:? _d_run_main [0xb5036844]
??:? [0xf13be14]
??:? __libc_start_main [0xb479c1c0]
??:? [0xf10a2a9]
Neoprávn&#283;ný p&#345;ístup do pam&#283;ti (SIGSEGV)
```

I have also repaired suspend (black screen after waking up) - I don't actually know, how... Could these things be connected with each other? 

How to solve it?

Thanks,

Marek

---

### Post by pema001 on 2018-03-10
actually, the error was caused by damaged file - I started to resync all, hope it's gonna work

---

### Post by lepolau on 2018-05-30
Hi,
What are you install for syncing with onedrive business ?

---

