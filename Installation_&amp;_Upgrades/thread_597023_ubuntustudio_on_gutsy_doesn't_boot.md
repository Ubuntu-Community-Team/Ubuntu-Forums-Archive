---
title: "ubuntustudio on gutsy doesn't boot"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by phonky on 2007-10-30
Hi

I upgraded to gutsy on release.

I'm running an Apple MacBook Pro, dual booting between Mac and Ubuntu via rEFIt and grub.
I use my Mac installation for audio production.

I wanted to give ubuntustudio a try, so I installed (from gutsy!)

```
sudo apt-get install ubuntustudio-audio ubuntustudio-plugins
```

This installed a new kernel in my menu.lst, the 2.6.22-14-rt realtime kernel.
Booting that kernel doesn't work though, I get:

[ 22.952909] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 23.365116] Kernel panic - not syncinc: IO-APIC + timer doesn't work! Boot with apic=debug and report, then try to boot with noapic option

And I have to switch the power off and reboot completely and boot the standard generic gutsy kernel.

Any ideas what could be done? I booted with noapic by the way, but the results were disappointing: blurred icons, sluggish performance...

Thank you for any help, greatly appreciated.

---

### Post by crazyness003 on 2008-01-03
Even tho this is an old thread, I just installed U studio on my laptop and I cannot boot with apic. I need the boot param "noapic" in order to get into the realtime kernel 2.6.22-14-rt. Fortunatley, i have no decrease in performance, in fact it runs a whole lot faster than my xp boot

I dont know ifthis will help but try all of these boot param options 
noapic
nolapic
pci=noapic
acpi=off
ide=nodma

do one at a time

---

### Post by phonky on 2008-01-12
Thank you,
even if this is an old thread comments greatly appreciated.

As stated in the previous post already, I booted with the noapic option; however, this results in a very sluggish graphic performance and there seems to be also no timing in audio at all, there is no realtime at all, the audio stream is absolutely not coherent and steady - just horrible, unusable. 

It seems APIC is very important here, and without this kernel doesn't boot on my machine.

---

