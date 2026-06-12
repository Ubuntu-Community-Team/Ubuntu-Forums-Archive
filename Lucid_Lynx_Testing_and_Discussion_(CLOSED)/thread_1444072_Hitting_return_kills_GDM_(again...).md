---
title: "Hitting return kills GDM (again...)"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-03-31
Hey guys,
Has anyone found that this bug is back with a vengeance from earlier on in the development cycle?  Hitting return for me occassionally crashes GDM and takes me to tty8, so that if I switch back to tty7 it's just blank and unusable.
Anyone else?

---

### Post by macstevejb on 2010-04-01
see this thread:

[http://ubuntuforums.org/showthread.php?t=1436466](http://ubuntuforums.org/showthread.php?t=1436466)

regards:D

---

### Post by JCoster on 2010-04-01
Hey thanks for your reply, although I run an ATI card [with the radeon driver]?

---

### Post by JCoster on 2010-04-01
And this is what appears in [what i think is the right] log file:
```

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7fba91ac8000+0xf8f0) [0x7fba91ad78f0]
3: /lib/libc.so.6 (__select+0x13) [0x7fba90880fd3]
4: /usr/bin/X (WaitForSomething+0x1ba) [0x45f97a]
5: /usr/bin/X (0x400000+0x30952) [0x430952]
6: /usr/bin/X (0x400000+0x261aa) [0x4261aa]
7: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7fba907c0c4d]
8: /usr/bin/X (0x400000+0x25d59) [0x425d59]

Caught signal 3 (Quit). Server aborting

```

---

