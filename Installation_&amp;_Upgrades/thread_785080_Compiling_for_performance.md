---
title: "Compiling for performance"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by gsiliceo on 2008-05-07
DOes anybody know where can i get information to compile ubuntu for my specific cpu with the CK(con kolivas) patchs? i badly need the performance in hardy heron.

Ok i'll be more specific, i need to know what architechture my cpu is, i'm confused with the i386 and i686 and i586, is there a way to know for sure?

Has anybody tried con kolivas patch?

Will ubuntu become unstable if i compile my own kernel? using the Kernel Master Thread?

---

### Post by madtinkerer on 2008-05-07
The ck patchset hasn't been active since the 2.6.22 kernel release.  You can't patch a newer version of the kernel with it, so you can't compile a new kernel for Hardy with the ck patchset.  I think most of the set was integrated into the regular kernel in 2.6.22 anyway, although I am not sure about that.

What CPU does your computer have?  It's probably i686.  Honestly, you're not going to get a huge performance increase by compiling a new kernel or recompiling all the ubuntu packages as i686.  If you're having performance problems, look at increasing your ram or optimizing your hardware setup.

---

### Post by gsiliceo on 2008-05-07
The number of opened apps and services is virtually the same since gutsy, but the overall performance is worst, i'll try using the 2.6.22 kernel then. Any performance improvement even 1% is acceptable for me at this point.

---

### Post by Lord Landis on 2008-05-07
I haven't compiled a custom kernel on my Hardy install, but I did so for Gutsy.  While performance wasn't that much better, I managed to save myself about 50 megs of RAM (this is on a system that only has 512).  I didn't have any problems when I followed what was in the master kernel thread, but I will caution you that, depending on your hardware, it can take hours to recompile.

To determine your exact hardware, code:
```
uname -mp
```

That will show you the processor type and machine type.  It will most likely return either i386 or i686.  If i386, use the 32-bit kernel.  If i686, use 64.

---

### Post by madtinkerer on 2008-05-07
i686 does not mean the cpu is a 64 bit cpu.  My P4 is reported as i686 but it is not a 64 bit cpu.  

You're welcome to try to compile your own kernel but I really don't think it will make a big performance difference.  You should post your hardware here and perhaps people can suggest some tweaks.

---

