---
title: "Kernel Panic - not syncing"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Norco_39 on 2006-12-23
I am having troubles installing Ubuntu 6.06 and would like to know what the problem is. I would like to first let you all know that I have posted about my problems before but have not received any useful help. I have been told to update my Bios and use the newer version of Ubuntu. I have tried updating by Bios and I still get the same error, and I have tried installing FC6 as well but I still get the same error. Also i have no blank c.d.'s to burn the newest version of Ubuntu on. Anyway, here is my problem, when I boot from the live c.d., which I ordered off the internet, I go to start/install and then I get this error "[17179569.756000] Kernel Panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option" I have tried exactly that but when I do the 'apic=debug' I don't know what to do, and then after I boot with the 'noapic' option I get this error "[17179570.604000] Kernel Panic - not syncing: VFS: unable to mount the root fs on unknown - block (8,3). I don't know what that means, and am so frustrated. I would love to have this done for the new year, before school starts again. Any help will be greatly appreciated.
__________________
Motherboard: M2N-E, CPU: AMD 64 Athlon XP, Video Card: XFX GeForce 7900 GS, Sound Card: Creative Sounblaster X-Fi Platinum, PSU: Antec TruePower 2.0 550 W, Hard-drive: 2x 250Gb Seagate Raid 0, Memory: Mushkin 2Gb

---

### Post by kidders on 2006-12-23
Hi there,

Guessing at the cause of this problem would very much be a shot in the dark, I'm afraid. There are far too many things that could be doing it. I hate to repeat suggestions you've already received, but if you're using outdated software with an outdated BIOS, using the latest Ubuntu with a fully upgraded BIOS would eliminate quite a lot of potential hardware-related issues, caused by invalid assumptions Linux might be making about your computer.

Your signature mentions RAID 0 ... is that emulated by your BIOS? If so, perhaps you could try turning that off, along with anything else you suspect might be causing difficulty, such as power management. Once things start to work for you, you can experiment with turning stuff back on, to identify your specific problem.

**Edit:** Btw, I presume you've got the correct version of Ubuntu for your CPU architecture ... always worth checking!

---

### Post by K.Mandla on 2006-12-24
kidders is right, although it might be tough to hear the same suggestions so many times over and over. Personally, I've had problems before where certain hardware simply refused to work with Ubuntu, and it's altogether possible that you're experiencing the same thing. 

I'm assuming your system is the one in your sig; in that case I would suggest removing some of the components to see if you can pin down what's causing the kernel panic. Try it without the sound card, then without the video card, then with different hard drives, and so forth. Chances are there is some sort of conflict between components that's causing the kernel panic.

If you do manage to pin down one item that is giving you trouble ... well, you can study up on it and see if anyone has managed to make it work, or you can try replacing it with something else. Your system looks very new; remember that Linux starts out at a disadvantage since few manufacturers will share driver information. So a lot of cutting-edge hardware needs time to be studied and tested before it works with Linux.

I hope this hasn't been discouraging. Play around some more, and see if there's one thing that you can subtract and get Ubuntu working. Good luck!

---

### Post by kidders on 2006-12-24
Hey again,

I just wanted to add one more thing. If you do find what's giving you grief, please post it.

[LIST]
[*]Other users will benefit from your experience.
[*]I'd be happy to help you work around the problem ... the solution might be as simple as tweaking your kernel slightly :-)
[/LIST]

---

### Post by hemlut on 2006-12-24
> **Norco_39 said:**
> I am having troubles installing Ubuntu 6.06 and would like to know what the problem is. I would like to first let you all know that I have posted about my problems before but have not received any useful help. I have been told to update my Bios and use the newer version of Ubuntu. I have tried updating by Bios and I still get the same error, and I have tried installing FC6 as well but I still get the same error. Also i have no blank c.d.'s to burn the newest version of Ubuntu on. Anyway, here is my problem, when I boot from the live c.d., which I ordered off the internet, I go to start/install and then I get this error "[17179569.756000] Kernel Panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option" I have tried exactly that but when I do the 'apic=debug' I don't know what to do, and then after I boot with the 'noapic' option I get this error "[17179570.604000] Kernel Panic - not syncing: VFS: unable to mount the root fs on unknown - block (8,3). I don't know what that means, and am so frustrated. I would love to have this done for the new year, before school starts again. Any help will be greatly appreciated.
__________________
Motherboard: M2N-E, CPU: AMD 64 Athlon XP, Video Card: XFX GeForce 7900 GS, Sound Card: Creative Sounblaster X-Fi Platinum, PSU: Antec TruePower 2.0 550 W, Hard-drive: 2x 250Gb Seagate Raid 0, Memory: Mushkin 2Gb

There is another thread about the IO-APIC issue here:
[http://ubuntuforums.org/showthread.php?t=323600](http://ubuntuforums.org/showthread.php?t=323600)

the bugreport at launchpad.net is here:
[https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/76989](https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/76989)

---

### Post by udiopz on 2006-12-24
I have a similar problem concerning to IO-APIC in my new laptop bought a few days ago.
when i boot i receive the message "mp-bios bug: 8254 timer not connected to io-apic". after this, sometimes the boot process stops.. but generally it continue to run (during the remaining boot process, EVERY TIME ubuntu checks all filesystems.. and this activity requires EVERY TIME some minutes).

furthermore, if I boot with special options like noapic, there is the Kernel Panic .

i attach some quotes from dmesg:
```

[4294670.901000] ACPI: Looking for DSDT ... not found!
[4294670.931000] ENABLING IO-APIC IRQs
[4294670.932000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294670.934000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[4294670.934000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[4294670.934000] ...trying to set up timer as Virtual Wire IRQ... failed.
[4294670.934000] ...trying to set up timer as ExtINT IRQ... works.
...
[4294687.386000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294687.401000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
...
[4294850.805000]   Error calling BSTS
[4294850.805000]   A6M model detected, unsupported, trying default values, supply the developers with your DSDT

```

thank you very much and merry christmas :p

---

### Post by hemlut on 2006-12-24
> **udiopz said:**
> I have a similar problem concerning to IO-APIC in my new laptop bought a few days ago.
when i boot i receive the message "mp-bios bug: 8254 timer not connected to io-apic". after this, sometimes the boot process stops.. but generally it continue to run (during the remaining boot process, EVERY TIME ubuntu checks all filesystems.. and this activity requires EVERY TIME some minutes).

furthermore, if I boot with special options like noapic, there is the Kernel Panic .

i attach some quotes from dmesg:
```

[4294670.901000] ACPI: Looking for DSDT ... not found!
[4294670.931000] ENABLING IO-APIC IRQs
[4294670.932000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294670.934000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[4294670.934000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[4294670.934000] ...trying to set up timer as Virtual Wire IRQ... failed.
[4294670.934000] ...trying to set up timer as ExtINT IRQ... works.
...
[4294687.386000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294687.401000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
...
[4294850.805000]   Error calling BSTS
[4294850.805000]   A6M model detected, unsupported, trying default values, supply the developers with your DSDT

```

thank you very much and merry christmas :p

Seems to be the same problem, if you have anything to add to the bugreport feel free to do so. If more people have the problem they will try to fix it sooner.

---

