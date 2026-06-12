---
title: "686 or 386 kernel??"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by Jabran Asghar on 2006-08-05
Hi,

What is difference between 686 and 386 versions of kernels? How to install the 686 version (I see by default 386 kernel on my box, P4 3GHz)?

Will there be any performanc upgrades for the 686 one?

Thanks for any information.

Jabran

---

### Post by Jagot on 2006-08-05
686 is optimised for newer processors - in fact PPro/Celeron/PII/PIII/PIV, and supports newer features such as dual core processors.  386 is compatible with pretty much everything which is why it is the default kernel supplied with Ubuntu.

To install it, from Terminal:

```
sudo aptitude update
sudo aptitude install linux-686
```

You may get some performance increase, but unless you're doing something very processor intensive it won't be that noticeable.

---

### Post by Jabran Asghar on 2006-08-05
I just installed the 686 version. But now Nvidia latest drivers 1.0-8762 will not load ( I reinstalled them, linux headers also reinstalled ), how can I solve this?

---

### Post by Jabran Asghar on 2006-08-05
No problem :-) got it solved. Just needed to reinstall nvidia-glx.

---

