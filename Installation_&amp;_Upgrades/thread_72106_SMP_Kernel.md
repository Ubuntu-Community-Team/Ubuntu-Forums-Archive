---
title: "SMP Kernel"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-10-05
I would like to install Ubuntu with a SMP Kernel to take advantage of my hardware. It does not appear that this is an option when installing from scratch.

Can I achieve this with the install CD or do I need to download it?

If I need to download it, where can I get it from (I need a URL so I can download from another machine as my wireless is not working yet)?

Thanks

Mark.

---

### Post by jordilin on 2005-10-06
I had the same question as you when I decided to install Ubuntu. In the version 5.1 I have installed a new kernel by searching smp as follows: # apt-cache search smp 
then appears some packages on the screen, one of them being linux-image-2.6.12-9-686-smp; then I made #apt-get install linux-image-2.6.12-9-smp; and it upgraded my kernel to the new smp one. Following this, I booted the computer and that's all. You can obtain the version by doing: uname -r. By the way, I have installed the smp kernel from the net, not from the install cd.

---

