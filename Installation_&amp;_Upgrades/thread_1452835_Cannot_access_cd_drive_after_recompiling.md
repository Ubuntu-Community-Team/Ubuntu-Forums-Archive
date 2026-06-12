---
title: "Cannot access cd drive after recompiling"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by Minsky on 2010-04-12
I'll be glad if someone can help me with this, I've compiled and installed kernel 2.6.31.13 in Karmic and it works fine apart from that I cannot access the cd/dvd drive. When I press the eject button, the tray slides out and immediately closes again. When I manage to insert a cd into the tray before it closes, the cd doesn't autorun as it should, and I cannot access the contents using Nautilus. When I reboot and switch back to the previous installation, the cd drive works normally. I realise that this is probably due to a setting that I should have made in the .conf file, but is there a way to fix this without recompiling, and also, what option should I have enabled in the .conf file to prevent this from happening? Btw, the cd drive is on a EIDE interface.

---

### Post by khelben1979 on 2010-04-12
Why not use one of the provided Linux kernels which is provided by the distribution?

If something is wrong with the compiled kernel it's something which isn't really part of Ubuntu since it's a custom kernel. Maybe you need more experience in compiling kernels?

[Kernel/Compile - Community docs]("https://help.ubuntu.com/community/Kernel/Compile").

---

### Post by Minsky on 2010-04-12
Thanks for replying Khelben, I wanted to have a go at tailoring the kernel to my system which is why I compiled, and I must admit that I am a novice at compiling kernels. Apart from the CD drive problem, its been pretty much a successful experience in that I've noticed Ubuntu to be a bit more responsive and also a feature that didn't work before has been enabled (Switch User now works). I know the problem isn't through a fault in the OS, but I'm sure that many Ubuntu users have had a go at compiling the kernel and that some may have made a similar error to mine, which is why I've asked for help here. So I'm still stuck, if anyone can help, I'd be very grateful.

---

