---
title: "Can't boot Ubuntu more recent than 10.10?"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by ivotedforkodos on 2013-01-02
I have a computer that is still currently running Ubuntu 10.10. I have tried to upgrade [several]("http://ubuntuforums.org/showthread.php?t=1909732&highlight=ivotedforkodos") [times]("http://ubuntuforums.org/showthread.php?t=1874905&highlight=ivotedforkodos"), but I haven't been able to get this machine to reliably boot with any version of Ubuntu newer than 10.10. 

Is there any reason why my hardware would not be able to boot more recent versions of the Linux kernel? I'm currently running 2.6.35-32-generic on amd64. 

When I try to boot from a 12.10 USB key, I see the purplish screen with the keyboard and accessibility icon, then a black screen with a flashing cursor at the time, then a wipe to a black screen -- and then the machine just hangs. There is no sign of any activity (disk lights, etc.). The same thing happens with a 12.04.1 USB key, although this time the hang is on a black screen with a small cursor that does not blink. I've even tried this without any HDs attached to the machine, so I don't think GRUB is the problem. 

What other options do I have if I can't boot from a USB drive?

Thanks.

---

### Post by oldfred on 2013-01-03
What video card do you have?

I have nVidia and have to use nomodeset. Both to boot flash drive and on first boot after install.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ivotedforkodos on 2013-01-03
> **oldfred said:**
> What video card do you have?

nVidia GeForce GTX 460

> **oldfred said:**
> I have nVidia and have to use nomodeset. Both to boot flash drive and on first boot after install.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thanks for the suggestion. I tried a few different Boot options, including "nomodeset", but nothing worked. 

Any other ideas?

---

### Post by oldfred on 2013-01-03
With nVidia card you definitely need the nomodeset. If you remove the quiet splash do you see commands/system loading process? 
Sometimes you might see if another driver is causing the issue and then can add another boot parameter for that. Often not the last thing posted which seems for most to be checking battery state even if no battery.

---

### Post by ivotedforkodos on 2013-01-03
> **oldfred said:**
> With nVidia card you definitely need the nomodeset. If you remove the quiet splash do you see commands/system loading process? 
Sometimes you might see if another driver is causing the issue and then can add another boot parameter for that. Often not the last thing posted which seems for most to be checking battery state even if no battery.

Hmm...now I'm thinking that this may be related to ACPI. I was able to boot once from the USB stick, but I haven't been able to reproduce it.

---

