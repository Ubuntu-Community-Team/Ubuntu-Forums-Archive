---
title: "Banshee crashes on site"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eaterjolly on 2010-04-08
everytime i try to launch banshee it crashes. the terminal gave me this as the ending partion of code if you think i should submet more of the code please tell me i just don't want to flood the thread ```
#18 0x00007fcf225decad in ?? () from /lib/libc.so.6
#19 0x000000004070d424 in ?? ()
#20 0x00007fcf0b071000 in ?? ()
#21 0x00007fcf180ce340 in ?? ()
#22 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
```

---

### Post by Anduu on 2010-04-09
Are you using the Mirage extension by chance?

It is not compatible with the latest version of Banshee.Uninstall it and Banshee should work again.

---

### Post by fluteflute on 2010-04-09
As said above try removing "banshee-extension-mirage"

---

### Post by eaterjolly on 2010-04-10
> **Anduu said:**
> Are you using the Mirage extension by chance?

It is not compatible with the latest version of Banshee.Uninstall it and Banshee should work again.

really it says version 1.6.0.1

---

### Post by Anduu on 2010-04-10
> **eaterjolly said:**
> really it says version 1.6.0.1

Yes it seems they have finally updated mirage...I just installed it again and no more crash for me.

Are you still crashing?

---

