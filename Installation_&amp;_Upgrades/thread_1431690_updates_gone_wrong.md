---
title: "updates gone wrong"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by hectorbls on 2010-03-16
Hello, I ran the update manager today and it updated several things including the kernel and the x-server setting and now when I boot my ubuntu it get an error message telling me that it is going to start ubuntu in a "low graphics mode". I'm running ubuntu ultimate 2.5 which is karmic koala on an HP with an AMD Phenom x4 with an integrated card graphics card ATI 3200HD.

Originally, when I first installed ubuntu, I had to install the ATI proprietary drivers version 9 to give me the correct resolution. It worked just fine for quite some time now. However, after the updates from the update manager today, I thought that a newer version of the ATI drivers should be available to fix this. I found version 10 of the drivers on the ATI website and installed them. Now the problem got worse as I lost the GNOME panels.

How can I fix the update or can I go back to my previous settings?

Thanks in advance

---

### Post by ConDsenXieN on 2010-03-16
Any way you can remove the updates via Synaptic? I had a kernel update that was incredibly unstable, marking the updated kernel for complete removal fixed the constant crashes I was experiencing. Could work, but don't quote me on it, mate.

Good luck!

---

### Post by hectorbls on 2010-03-17
thanks for the advice, after looking around I found a solution to the problem with the steps on this ubuntu tip

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

It contains instructions on how to purge all xorgs and auto-configure a new one. Then I reinstalled the old proprietary drivers and it fixed the problem

---

### Post by ConDsenXieN on 2010-03-17
Good stuff. Hopefully the next update won't make this problem again. :P

Out of curiosity, was it a normal update or one of the "proposed" updates? If you can tell me exactly what update it was that threw your system off, I'll keep an eye out to avoid it myself.

---

### Post by hectorbls on 2010-03-18
I don't remember very well but I think it was one of the "proposed" because I remember it being towards the bottom in the update manager list.

---

### Post by U&amp;T on 2010-03-18
Thanks!

---

