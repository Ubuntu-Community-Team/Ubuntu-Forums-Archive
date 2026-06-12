---
title: "No sound after install"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by Gaijinda on 2008-08-29
Hello,

I am new to ubuntu and the whole linux family so I apologize in advance for this being a newbie question.  

I finally switched over from the dark side just the other day and decided to install ubuntu to my laptop.  I have a Mobile AMD Athlon 64-bit 3400+ Processor, so I first installed the 64 bit version of ubuntu.  Everything worked fine except it ran extremely slow.  After looking up that problem, I decided to try the 32-bit version.    The slow downs and freeze ups have been alleviated, but now I no longer have sound.  I tried to reinstall and still nothing.  

Does anyone have any suggestions on how to fix this issue?  Since I just installed linux yesterday, I am pretty new to everything and still pretty stupid....gomen m(_ _)m

If it helps here is my system specs:

Processor: Mobile AMD Athlon&#8482; 64-bit 3400+ Processor 2.2 GHz 
Chipset:   ATI RS480M
Memory:    512 MB 333 MHz DDR 
Video:     ATI Radeon® Xpress 200M Graphics
Audio:     AC '97 2.3 Compliant Audio

Thanks

---

### Post by spiderbatdad on 2008-08-29
Try the command:```
alsamixer
```
make sure both master and PCM are up. If no luck...
Try this command:```
asoundconf list
```Hopefully this produces a card parameter. Then run:```
asoundconf set-default-card <parameter>
```reboot.
Try the gui found in System>>Preferences>>Sound, and select alsa for the playbacks. Make sure the packages below are installed via synaptic package manager.

---

