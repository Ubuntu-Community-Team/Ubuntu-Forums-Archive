---
title: "cannot install due to bios bug"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by dj_burns on 2006-10-27
i have recently purchased a new machine and have been keen to install ubuntu on it. unfortunately the pc hangs when i try to run the install from the live cd and when i tweak the boot it gives me a 'bios bug no explicit irq entries' error message and a 'local apic #0 not detected' and then stops.

being new to linux i have no idea what to do, or if my hardware is even supported. i have a intel g965 lga 775 running a pentium d 915      
2.8 GHz processor. any help would be greatly appreciated

thanks

dj_burns

---

### Post by Kateikyoushi on 2006-10-27
Try to boot with these, one by one.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by dj_burns on 2006-10-27
thanks

i'll give those a try and hold thumbs.

---

### Post by faddat on 2006-11-03
Hey, I wanted to let you know that I am having the same problem.  According to [this]("http://www.suseforums.net/index.php?showtopic=25955") forum post, the problem is with the kernel version.  Anything with a Kernel 2.6.18 or above should work.  Right now we are trying the OpenSUSE 10.2 Beta1  installer CD, I'll let you know if that does the trick.  You might also want to try Fedora, which has the higher kernel version as well.

---

### Post by xp_newbie on 2006-11-03
> **Kateikyoushi said:**
> 
Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

Yes, one (or more) of this options will eventually let him boot Ubuntu on his machine, but it also means that once installed (into hard disk), *the system will not use the hardware efficiently*.

I myself encountered at least two such cases and I must admit that it is becoming very frustrating and discouraging. [Even the Linux kernel developers themselves have no answer to this]("http://groups.google.com/group/linux.kernel/browse_frm/thread/9c4e5121e136e3ba/de6748b62e5165f4?&hl=en#de6748b62e5165f4").

If Linux cannot be installed to be run **optimally** on a given hardware, meaning that I have to buy a new PC that is "Linux approved", I'd rather pay Microsoft for a Windows license, which costs much less than a new PC...

Please don't be offended by my last statement: I am proponent of Linux like everyone else here, but we as a Linux enthusiasts must face the truth and relay it to the kernel developers to give it better chance of succeeding in the desktop arena.

If you have tips, tricks and/or ideas that can alleviate the problem, I would appreciate sharing them here.

Alex

---

