---
title: "Problem recompiling kernel"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by caburrows on 2008-02-19
don't worry, this isn't like all the other "how do i recompile the kernel" questions... (at least i couldn't find a solution for this problem anywhere)
I'm running gutsy with linux-headers-2.6.22-14, and there are a few changes that i wanted to make to the kernel (out of pickiness)...
after I make the changes I want to the configuration, I try to compile the kernel, but I keep on getting the following error:

  SYMLINK include/asm -> include/asm-i386
make[2]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [debian/stamp-kernel-conf] Error 2

I thought it would have been because of the changes I made, but no matter what I try, it just keeps on giving me that... (and I've tried to find an answer, but can't understand what's wrong)

thanks in advance for any help :)

---

