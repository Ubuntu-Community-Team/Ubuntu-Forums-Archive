---
title: "I saw that the latest Linux kernel is 2.6.25.6; would it be a good idea to upgrade?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2008-06-10
It appears that Hardy's kernel is 2.6.24-18.  I have seen that the latest Linux kernel is 2.6.25.6 from this location: [http://www.kernel.org/]("http://www.kernel.org/")
Would it be advisable to *not* upgrade to this kernel for any reason?
I would need help doing so; for some reason I do not think downloading the archive and unpacking it would be enough.

Thanks.

---

### Post by dstew on 2008-06-10
No, there is usually no reason to upgrade to the newest kernel. The reason you have to be careful about this, is that the hardware drivers are made *after* a new kernel is made, usually. So, the Hardy kernel 2.6.24 has drivers matched to it. The kernel is constrained by the drivers that are present in the distribution. If you installed a 2.6.25 kernel, you might find that some of your hardware stops working. It is best to wait for kernel upgrades that are offered by the Update Manager.

That said, sometimes you have a piece of hardware that will not work with a certain kernel. If you really need that hardware, then sometimes you have to compile a later kernel. But, that might cause problems with other hardware.

---

