---
title: "Hibernate problem with desktop machine..."
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by cruiserandmax on 2007-08-08
I just installed 7.04 Feisty on and MSI Axis 700 (VIA C7 CPU, VIA700 VT8237R+ chipset)... I'm having trouble waking the machine back up via keyboard, mouse, or PCI interrupt (WOL). It seems after ubuntu hibernates the ONLY way the machine will wake up is via the power button on the case!

The quetion- is this likely a ubuntu issue, or a hardware/bios issue? In the bios- ACPI is enabled, ACPI standby state is S3, resume by PS/2 keyboard enabled, resume by PS/2 mouse enabled, resume by PCI device enabled.

Thanks for any thoughts...

---

### Post by mikeleawilson on 2007-08-09
Surely this is correct behaviour? Hibernate isn't working at all on my machine for some reason (which is why I came here), but if it's the same as Windows, then once you've hibernated, the machine is off, (with all the memory state saved on the hard disk) and the only way you can turn it on again is by pressing the power button. The memory is then restored from the hard disk, and you carry on where you left off. You're probably confusing hibernate and suspend. After a suspend (which I think is called sleep on Windows) the machine is not completely off, but has enough of the circuitry powered up to detect keyboard presses or mouse clicks, so these can wake it up. In this state, if you turn the power off at the wall,  it will forget everything, and you will have to log in again.

---

### Post by Mach1US on 2007-08-09
mikeleawilson  is absolutely correct and as far as fixing suspend this how to worked for me 100%
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by cruiserandmax on 2007-08-11
I have a windows XP machine that hibernates (completely powers off-writing entire state of memory to disk using basically no power), and still allows movement of mouse, touch of keyboard, or WOL signal to "wake up". This is using an Asus K8V SE motherboard (Award bios)... So I am positive this is possible- I'm just trying to determine if Ubuntu, or my new MSI machine (which also has an Award bios with identical settings as the K8V SE) is the problem here...

---

### Post by cruiserandmax on 2007-08-11
> **mikeleawilson said:**
> Surely this is correct behaviour? ...  if it's the same as Windows, then once you've hibernated, the machine is off, (with all the memory state saved on the hard disk) and the only way you can turn it on again is by pressing the power button. 

Not so in my Windows experience. I have a Windows XP install I have set to hibernate. When it hibernates (completely powers off with RAM state written to disk), it still allows mouse movement, keyboard input, or WOL to "power back on" and re-load the hibernate state from disk... So I'm just trying to figure out how to do this with ubuntu..

---

