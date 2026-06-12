---
title: "C Compiler error"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by bsdrocker on 2007-06-06
This may seen like a noob question to some - but I haven't used Linux in about 3 years...

When I was building my Snort source I received this error:

Checking for C compiler default output file name... configure: error: C compiler cannot create executables

Does any one have any ideas?

-bsdrocker...

I don't know if this belongs here - I was installing something so I just assumed...

---

### Post by taurus on 2007-06-06
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by bsdrocker on 2007-06-06
Thanks I'll give this a try! :p

---

### Post by bsdrocker on 2007-06-06
THANKS!! It worked perfect!

---

