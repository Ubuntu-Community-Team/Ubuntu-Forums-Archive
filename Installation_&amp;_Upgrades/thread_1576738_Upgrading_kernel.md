---
title: "Upgrading kernel"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by dakane on 2010-09-17
I have a wireless problem, and from searching, I get the impression that upgrading my kernel from 2.6.32 to at least 2.6.33 will fix it.  I don't see any newer kernels in Synaptic.  How do I do this?

---

### Post by snowpine on 2010-09-17
Welcome to the forums! Before you do anything rash :) I would recommend starting a new thread with the specifics of your wireless problem. It may be possible to get your wireless working under the supported 2.6.32 kernel. For example, you can go to System>Administration>Hardware Drivers, or you can search for your specific card on [the Ubuntu wiki]("http://wiki.ubuntu.com").

Should you come to the conclusion that a kernel upgrade is the only solution, the easiest way to get a different kernel is from the [Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). You'll need to find and download the correct linux-image for your architecture (either i386 or amd64), then double-click the downloaded .deb file to install it with the Gdebi package installer.

---

### Post by dakane on 2010-09-18
Thank you. I was having a hard time finding that page.

I updated the kernel, and probably should have taken your advice and started a thread about the wireless, since after updating the kernel, I did a bunch of other things and messed up my system.  But it all works now.

---

