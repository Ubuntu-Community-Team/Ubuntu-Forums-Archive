---
title: "Video Driver Question?"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by tealflame on 2012-05-14
I have a desktop pc with a PCI-E Visiontek ATI Radeon HD 4670 video card.

I have a fresh install of Ubuntu 12.04 64bit.  I installed the AMD driver from additional drivers.  Rebooted.  

For some reason under System Settings\Displays, It now shows I have a Laptop monitor.  Before I installed the driver, it showed the correct monitor.  This is a desktop computer and monitor.  

What can be wrong?  

Are the open source drivers for my card better to use than the closed source ones?

---

### Post by tealflame on 2012-05-15
After doing some research I learned that the open source drivers are more stable to use.  However, they also cause my ati card to run hotter.  It was around 61C in Ubuntu.  Windows Catalyst driver showed around 35C in Windows.  

So I installed the regular proprietary driver, (**not** the post release one), in Ubuntu through the Additional Drivers and now the temp is about 38C.  I haven't had any major glitches yet, (knock on wood).

:-\"

As for the display showing up as a laptop, I cannot find any info about it.  I'm guessing its like the "plug and play monitor" in Windows.

---

### Post by roelforg on 2012-05-15
> **tealflame said:**
> After doing some research I learned that the open source drivers are more stable to use.  However, they also cause my ati card to run hotter.  It was around 61C in Ubuntu.  Windows Catalyst driver showed around 35C in Windows.  

So I installed the regular proprietary driver, (**not** the post release one), in Ubuntu through the Additional Drivers and now the temp is about 38C.  I haven't had any major glitches yet, (knock on wood).

:-\"

As for the display showing up as a laptop, I cannot find any info about it.  I'm guessing its like the "plug and play monitor" in Windows.

I too have an ati card.
```

sudo amdcccle

```
In a terminal will launch the amd control, it'll let you control how the monitors are used (the entry in dash doesn't work).

---

### Post by tealflame on 2012-05-15
Ok, thanks.  It shows the correct monitor in the amdcccle section.  I guess thats all that matters.  The Ubuntu Display section in System Settings shows laptop, must be a minor glitch.

---

