---
title: "How to find/install kernel 2.6.32-10"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by IceCap on 2010-01-17
Hi,

  I have a MythBuntu system running 9.10 and as many others I am having issues with my wireless card controlled by ndiswrapper (networks are detected but it is unable to obtain an IP address most of the time, once in a while it connects, it also has the "invalid cmd 12" issue which fix is described **[here]("http://ubuntuforums.org/showthread.php?t=1343847")**).

  So I found this thread **[here]("http://ubuntuforums.org/showthread.php?t=1343847&page=3")** (see post #30 on the bottom) and I'd like try upgrading the kernel to a version which Synaptics apparently doesn't offer.

  So my question is basically threefold.

[LIST=1]
[*] Where do I find/download the kernel (is there a way to use apt get ...)
[*] What method do I use to install it (I've found several directions on how to compile it, if someone could point to the most complete ones, I would appreciate it.
[*] If for some reason something goes wrong and I need to downgrade again, how do I do that (Synaptics?).
[/LIST]

  BTW, I can hook it up to the network through ethernet and ssh into it from my Mac Mini to work on it.

 Thanks in advance,

  IceCap

---

### Post by oldos2er on 2010-01-17
2.6.32-* kernels are in Lucid's (10.04) repositories: [http://packages.ubuntu.com/lucid/linux-image](http://packages.ubuntu.com/lucid/linux-image)

You risk breaking your system by installing it, just FYI.

---

