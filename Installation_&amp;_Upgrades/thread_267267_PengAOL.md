---
title: "PengAOL?"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by Vekemi on 2006-09-28
I'm using PengAOL to try to connect through AOL dialup, but I get this error when I ```
./recompile
```

._.

```

In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/iostream.h:31,
                 from cclienttoaol30.h:24,
                 from kernel30.h:50,
                 fmake[2]: Leaving directory `/home/vekemi/peng/peng'
make[1]: Leaving directory `/home/vekemi/peng'

/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:226: error: ISO C++ forbids declaration of ‘CAolCmd30’ with no type
kernel30.h:226: error: expected ‘;’ before ‘*’ token
make[2]: *** [threadELV3.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2

```

---

### Post by Fatjoint on 2006-09-28
> **Vekemi said:**
> I'm using PengAOL to try to connect through AOL dialup, but I get this error when I ```
./recompile
```

._.

```

In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/iostream.h:31,
                 from cclienttoaol30.h:24,
                 from kernel30.h:50,
                 fmake[2]: Leaving directory `/home/vekemi/peng/peng'
make[1]: Leaving directory `/home/vekemi/peng'

/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:226: error: ISO C++ forbids declaration of ‘CAolCmd30’ with no type
kernel30.h:226: error: expected ‘;’ before ‘*’ token
make[2]: *** [threadELV3.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2

```


Have to ask, but did you continue on and try to connect?

In my experience with C, and C++ warnings don't necessarily mean failure.

---

### Post by skymt on 2006-09-28
Those aren't warnings, they're errors (failures). From the error message, it looks like an actual bug in the code. You need to contact the developers for help on this one.

---

### Post by Fatjoint on 2006-09-28
> **skymt said:**
> Those aren't warnings, they're errors (failures). From the error message, it looks like an actual bug in the code. You need to contact the developers for help on this one.

Gah... forget what I said above.  I scrolled the screen to look at what the warning was and didn't see the errors!

---

