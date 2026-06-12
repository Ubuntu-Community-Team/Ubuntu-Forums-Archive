---
title: "Does not boot fully"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by xkookooman on 2006-10-25
Booting ubuntu is ok, but when I want to install it, it takes about a minutue, and then the sound comes out, but there is no image.  I tried all the different seettings, but nothing works.  Could this be a driver related issue? I have Anthlon X2 3800 with two Nvidia 7800gtx(s) in SLI and 1024 mb of RAM.

---

### Post by Kateikyoushi on 2006-10-25
Did you try safe video mode ? I think it's because of the sli.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

If nothing seems to work try the alternate install cd which uses text mode for installation.

---

