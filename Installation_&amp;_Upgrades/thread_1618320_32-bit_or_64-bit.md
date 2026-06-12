---
title: "32-bit or 64-bit?"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by twistedwire on 2010-11-10
Hey guys, here's a quick question...I can get the version etc, etc....but, due to a lack of memory, how can I tell if I'm running 32-bit or 64-bit?  :confused:...

Thanks!

---

### Post by wojox on 2010-11-10
Look at the kernel:


```
uname -a
```

---

### Post by twistedwire on 2010-11-10
Did a uname -a:

kevin@portable-linux:~$ uname -a
Linux portable-linux 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
kevin@portable-linux:~$ 

how does it explain 32-bit vs 64-bit?

Thanks for the fast reply!!

---

### Post by dino99 on 2010-11-10
thats 32, open synaptic and see how kernel are named

---

### Post by TBABill on 2010-11-10
i686 is another name for a 32 bit Intel compatible OS...think of the days of 286, 386, 486 processors. If it was a 64 bit version it would state x86_64.

---

