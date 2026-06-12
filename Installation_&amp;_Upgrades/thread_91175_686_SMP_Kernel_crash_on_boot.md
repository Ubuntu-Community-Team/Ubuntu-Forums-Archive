---
title: "686 SMP Kernel crash on boot"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by flobbleobble on 2005-11-16
Hi

I've just installed the 686-SMP kernel using synaptic package manager. I was originally using the default 386 kernel. The system hangs at various points in the boot process when I use this kernel. With the 386 there's still no problem. I've tried switching off various services at bootup without any change.

I can use the 686 kernel without problems - it's just the 386-SMP one.

My CPU is a P4 530 HT. Hyperthreading works fine in Windows so I don't think it's a CPU problem.

I haven't found anyone with the same problem on the forums - their systems seem to hang when the system has booted.

Any suggestions?

PS. It seems that the boot process stops when the ALSA service starts. The screen goes blank and that's it. This happens consistently.

---

### Post by muammarelkhatib on 2005-12-22
I've the same problem. I had to compile a version of the kernel (2.6.13) by myself and it works. But now the cdrom doesn't work.

Muammar El Khatib.
Linux user: 403107.

---

