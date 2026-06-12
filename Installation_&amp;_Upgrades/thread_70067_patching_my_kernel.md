---
title: "patching my kernel"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-09-28
i have a few questions about patching my kernel:
1.if i patch the ubuntu optimized kernel to make it 2.6.13.2 will it still retain all of the previous patches?
2. where can i get this patch? i know i can get the kernel itself from kernel.org, but where can i get the patch?

---

### Post by az on 2005-09-28
I think what you are refering to is a diff.  It is sort of a patch that applies to a pristine kernel to go to the next version.  You cannot use them with patched (distribution) kernels.

---

### Post by mlomker on 2005-09-28
Your options are to either wait for them to put a kernel update in Synaptic (they are named linux-image-*) or compile your own without Ubuntu's patches.  There are some how-to's on here for compiling your own kernel but it is time consuming and the results are often worse than where you started.  :)

---

### Post by Brando569 on 2005-09-28
yea im patching/recompiling kernels now cuz im finally (trying) to get bootsplash to work, i was gonna use 2.6.13.2 then realized that id have to apply all these patches and stuff, so i stuck with 2.6.10 and just patched that, hopefully it'll work

---

