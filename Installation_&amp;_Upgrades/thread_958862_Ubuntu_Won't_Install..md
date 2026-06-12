---
title: "Ubuntu Won't Install."
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by lonegeek on 2008-10-25
So my file server motherboard went out. So I pulled the drives, ram, video card. Put it into my amd xp 2200 and msi k7n2 motherboard. 

I've had ubuntu installed to this computer before.

Now with either 7.10 or 8.04 disc it locks up on the progress bar when i select install or live cd. Then the keyboard lights flash. 

Any ideas and help would be appreciated!

zach

---

### Post by JC Cheloven on 2008-10-25
Have you tried the options
noapic nolapic
at startup? Sometimes this helps with hardware locks. 

Also you can try pci=routeirq

If you think it could be a display problem, try vga=771 or (more severe) xdrvr=vesa

All these options may be given (among other situations) when booting from live cd, to test if some of them helps. Simply place one of them at a time at the end of the options line shown when booting.

You can include them (the useful options) in /boot/grub/menu.lst at a later time.

---

### Post by lonegeek on 2008-10-25
Well with -noapic -noalpic

it gets about 90 percent on the progress bar

then when i add pci=routeirq it only gets as far as without all of them.



Edit:

Loaded with -noalpic on its own, but then locked up in live cd.

---

### Post by lonegeek on 2008-10-27
None of the noapic, nolapic, or acpi=off work.

What doesn't make sense is that 6.06 worked just fine on this computer before.

---

### Post by lonegeek on 2008-10-27
What is completely crazy is that my old install of ubuntu boots up just fine, but seems to lock up if i play with it too much.

---

### Post by punkybouy on 2008-10-27
Have you tried using the alternate CD instead of the live CD?

---

### Post by lonegeek on 2008-10-28
> **punkybouy said:**
> Have you tried using the alternate CD instead of the live CD?

That won't make a difference. There is still a hardware lock up. Even with old installation on the hard drive it boots up but then locks up after about 30 minutes.

---

### Post by JC Cheloven on 2008-10-29
> **lonegeek said:**
> That won't make a difference. There is still a hardware lock up. Even with old installation on the hard drive it boots up but then locks up after about 30 minutes.

I didn't have previous experiences of real overheating on my own, although I played a little with the tools for that. This kind of hangs-after-a-while suggest overheating.

It could be cpu, ram or HD overheating. A few keywords: smartctl (for HD), powernowd (for cpu), and... sorry, can't remember for ram at this moment (do a search if you need it).

Hope this points you into the right direction.

---

