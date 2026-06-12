---
title: "PCI Error, Ubuntu Freezes On Load"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by deat on 2007-01-31
Ok, so I downloaded the Ubuntu i386 iso (6.10), burned it onto a CD, and when i booted into it, I selected the "Start or install Ubuntu" option, and things go fine for a second, then I get an error at the top of the screen that says:

PCI: Cannot allocate resource region 3 of device 0000:00:00.0

and it hangs for a moment, then goes into loading and auto configuring my monitor. Then Immediately after, it freezes and I have to reboot. After many tries at starting Ubuntu, I finally gave up and tried the Alternate iso. That didn't work either, it just hanged at the PCI error.

So I went back to the original CD and tried the second option, "Install in safe graphics mode". It finally load past where it froze before. I completely installed Ubuntu, then as I restarted my machine, it froze at the exact same spot it used to, after it configured the monitor.

I am wondering what the problem could possibly be?

I am running in the live CD (installer mode) right now, though I am very lucky i got it working again. It took numerous reboots to get into it.

Thanks!
Zach

---

### Post by dcstar on 2007-02-01
> **deat said:**
> Ok, so I downloaded the Ubuntu i386 iso (6.10), burned it onto a CD, and when i booted into it, I selected the "Start or install Ubuntu" option, and things go fine for a second, then I get an error at the top of the screen that says:

PCI: Cannot allocate resource region 3 of device 0000:00:00.0

and it hangs for a moment, then goes into loading and auto configuring my monitor. Then Immediately after, it freezes and I have to reboot. After many tries at starting Ubuntu, I finally gave up and tried the Alternate iso. That didn't work either, it just hanged at the PCI error.

So I went back to the original CD and tried the second option, "Install in safe graphics mode". It finally load past where it froze before. I completely installed Ubuntu, then as I restarted my machine, it froze at the exact same spot it used to, after it configured the monitor.

I am wondering what the problem could possibly be?

I am running in the live CD (installer mode) right now, though I am very lucky i got it working again. It took numerous reboots to get into it.

Thanks!
Zach

Do you have an internal video card as well as another one that is actually in use?

You may have to go into your BIOS and check that things are set up ok, there may be something that Ubuntu doesn't like.

Post your full hardware spec.

---

