---
title: "Kernil with all modules built in, now lots of errors on boot"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by dmb on 2006-05-18
Hello, I recently compile a kernel from source, and I compiled everything statically without any modules for performance reasons.  Everything is working, but now when I boot up, the usplash doesn't show, and I seen a ton of errors saying something like FATEL: Can't access /lib/modules/2.6.12/modules.dep or FATAL can't read: /lib/modules/2.6.12/modules.dep .  This doesn't appear in the boot log. Is there a way tos top it from autoloading all the the modules it usually loads, because I already compiled all the modules i need statically into the kernel. How do I fix this? Thanks.

---

### Post by NoUse on 2006-05-18
You may want to look over the wiki howto.
[https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)

---

### Post by dmb on 2006-05-18
I had followed that, and use make-kpkg.

---

