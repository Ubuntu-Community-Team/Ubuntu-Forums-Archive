---
title: "Updating kernel with synaptic?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by sicofante on 2007-03-10
I need a Kernel 2.19 or newer (hardware issues). I would like to know if it's possible to update from Edgy's kernel via synaptic, and how.

If not, what's the easiest way? Let's assume I can't compile sources.

Thanks for any help.

---

### Post by Captain_Riker on 2007-03-12
Hello,

what Hardware issues? Dual Core? BTW correct me, but there is no Kernel 2.19. You mean 2.6.19? Wait for Fesity Fawn. Should come along with a Kernel 2.6.18 or newer. That would solve issues with Dual Core.

But I don't think it's Dual Core. If you want to update your Kernel via Synaptic Ubuntu must at least be correctly installed. So how come you think a Kernel 2.6.19 would solve your problem? Or other (see above) what Hardware issues?

Greetings

---

### Post by sicofante on 2007-03-20
> **Captain_Riker said:**
> what Hardware issues?
Support for 3ware 9650SE RAID controller and Intel PRO/1000 PT Quad Port Gigabit Ethernet controller.

> BTW correct me, but there is no Kernel 2.19. You mean 2.6.19?Yes, sorry, I meant 2.6.19 or higher.

> Wait for Fesity Fawn.I can't.

> If you want to update your Kernel via Synaptic Ubuntu must at least be correctly installed.It is correctly installed. I just don't know what I have to do in order to update the kernel.

> So how come you think a Kernel 2.6.19 would solve your problem?
I'm using OpenFiler for this system. It works because its kernel is up to date, otherwise it wouldn't see the two cards mentioned above (that's documented, I can't simply "add a driver" for those cards). I would love to provide Ubuntu in the same system I'm building for my customer. The current Festy Fawn version doesn't even install on this system, that's why I would like to just update the kernel (I'm not going to compile it). If there's an easy way to update via Synaptic, nice, if not I'll ship the system without Ubuntu.

---

### Post by zvacet on 2007-03-20
Just try once.
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by sicofante on 2007-03-20
> **zvacet said:**
> Just try once.
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
I wouldn't call this "an easy way to update via Synaptic" but thanks anyway. I will try it later.

---

### Post by zvacet on 2007-03-20
I´m not an expert,but I never see or read of such option.Common sense telling me if that is possibility nobody will compile.

---

